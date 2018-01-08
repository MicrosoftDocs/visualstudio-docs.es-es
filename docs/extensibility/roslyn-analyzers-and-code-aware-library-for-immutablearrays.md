---
title: "Analizadores de Roslyn y la biblioteca de código para ImmutableArrays | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6870f1733d507f2cf46d196b2bba027b998b5ba4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizadores de Roslyn y la biblioteca de código para ImmutableArrays

El [.NET Compiler Platform](https://github.com/dotnet/roslyn) («Roslyn») le ayuda a crear bibliotecas de código.  Una biblioteca de código proporciona funcionalidad que puede usar y herramientas (analizadores Roslyn) para ayudarle a usar la biblioteca de la mejor manera o para evitar errores.  Este tema muestra cómo crear un analizador de Roslyn del mundo real para detectar errores comunes al usar el [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) paquete NuGet.  El ejemplo también muestra cómo proporcionar una revisión de código para un problema de código encontrado por el analizador.  Los usuarios ven correcciones de código en la interfaz de usuario de Visual Studio una bombilla y pueden aplicar una corrección para el código automáticamente.

## <a name="getting-started"></a>Introducción

Necesita lo siguiente para compilar este ejemplo:

* Visual Studio 2015 (no una versión Express Edition) o una versión posterior.  Puede usar gratuitamente [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  También puede, al instalar Visual Studio, comprobar herramientas de extensibilidad de Visual Studio en herramientas comunes para instalar el SDK al mismo tiempo.  Si ya ha instalado Visual Studio, también puede instalar este SDK, vaya al menú principal **archivo &#124; Nuevo &#124; Proyecto...** , elija C# en el panel de navegación izquierdo y, a continuación, elija extensibilidad.  Cuando se elige el "**instalar las herramientas de extensibilidad de Visual Studio**" plantilla de proyecto de la ruta de navegación, le pide que descargue e instale el SDK.
* [.NET compiler Platform («Roslyn») SDK](http://aka.ms/roslynsdktemplates).  También puede instalar este SDK, vaya al menú principal **archivo &#124; Nuevo &#124; Proyecto...** , eligiendo la opción **C#** en el panel de navegación izquierdo y, a continuación, elija **extensibilidad**.  Cuando se elige "**descargar el SDK de plataforma de compilador de .NET**" plantilla de proyecto de la ruta de navegación, le pide que descargue e instale el SDK.  Este SDK incluye la [Roslyn sintaxis visualizador](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Esta herramienta muy útil le ayuda a descubrir qué tipos de modelo de código debe buscar en el analizador.  Las llamadas de la infraestructura de analizador en el código para tipos de modelo de código concretos, por lo que el código solo se ejecuta cuando sea necesario y pueda centrarse únicamente en el análisis de código relevante.

## <a name="whats-the-problem"></a>¿Cuál es el problema?

Imagine que proporciona una biblioteca con ImmutableArray (por ejemplo, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) admite.  Los desarrolladores de C# tienen mucha experiencia con matrices. NET.  Sin embargo, debido a la naturaleza de técnicas de optimización y ImmutableArrays que se utiliza en la implementación, intuitions del programador de C# hacer que los usuarios de la biblioteca escribir código rota, como se explica a continuación.  Además, los usuarios no ven sus errores hasta el tiempo de ejecución, que no se utilizan en Visual Studio con .NET para la experiencia de calidad.

Los usuarios están familiarizados con la escritura de código similar al siguiente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Creación de matrices vacías para rellenar con las siguientes líneas de código y con la sintaxis de inicializador de colección son muy familiares a los desarrolladores de C#.  Sin embargo, escribir el mismo código para un ImmutableArray se bloquea en tiempo de ejecución:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

El primer error es debido a que la implementación de ImmutableArray utiliza una estructura para ajustar el almacenamiento de datos subyacente. Las estructuras deben tener constructores sin parámetros para que `default(T)` las expresiones pueden devolver structs con todos cero o null miembros.  Cuando el código tiene acceso a `b1.Length`, hay un valor null de tiempo de ejecución desreferencia de un error porque no hay ninguna matriz de almacenamiento subyacente de la estructura ImmutableArray.  La manera correcta para crear un ImmutableArray vacía es `ImmutableArray<int>.Empty`.

El error con inicializadores de colección se produce porque el método ImmutableArray.Add devuelve nuevas instancias cada vez que lo llama.  Dado que ImmutableArrays nunca cambian, cuando se agrega un nuevo elemento, se recibe un nuevo objeto ImmutableArray (que puede compartir el almacenamiento por motivos de rendimiento con un ImmutableArray previamente existente).  Dado que `b2` apunta a la primera ImmutableArray antes de llamar a `Add()` cinco veces, `b2` es el valor predeterminado es ImmutableArray.  Llamar a longitud en él también se bloquea con un valor null desreferencia de un error.  La manera correcta de inicializar un ImmutableArray sin llamar manualmente a agregar es usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Buscar tipos de nodos de la sintaxis pertinente para desencadenar el analizador

 Para empezar a generar el analizador, en primer lugar averiguar qué tipo de SyntaxNode necesita buscar. Iniciará el visualizador de sintaxis en el menú **vista &#124; Otras ventanas &#124; Visualizador de sintaxis Roslyn**.

Colocar el símbolo de intercalación del editor en la línea que declara `b1`.  Verá el visualizador de sintaxis muestra que se encuentra en un `LocalDeclarationStatement` nodo del árbol de sintaxis.  Este nodo tiene un `VariableDeclaration`, que a su vez tiene una `VariableDeclarator`, que a su vez tiene una `EqualsValueClause`y por último, hay un `ObjectCreationExpression`.  Cuando hace clic en el árbol de sintaxis visualizador de nodos, la sintaxis en la ventana del editor se resaltan para mostrar el código representado por ese nodo.  Los nombres de los tipos de sub SyntaxNode coinciden con los nombres utilizados en la gramática de C#.

## <a name="creating-the-analyzer-project"></a>Crear el proyecto de Analyzer

En el menú principal seleccione **archivo &#124; Nuevo &#124; Proyecto...** .  En el **nuevo proyecto** cuadro de diálogo, en **C#** proyectos en la barra de navegación izquierdo, elija extensibilidad y en el panel derecho, elija la **analizador con código corregir** proyecto plantilla.  Escriba un nombre y confirme el cuadro de diálogo.

La plantilla abre un archivo DiagnosticAnalyzer.cs.  Seleccione a ese editor ficha de búfer.  Este archivo tiene una clase de analizador (formato incorrecto del nombre que dio al proyecto) que se deriva de `DiagnosticAnalyzer` (un tipo Roslyn API).  La nueva clase tiene un `DiagnosticAnalyzerAttribute` declarar el analizador es relevante para el lenguaje C# para que el compilador detecta y carga el analizador.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Puede implementar un analizador utilizando Visual Basic que tenga como destino el código de C#, y viceversa.  Es más importante en el DiagnosticAnalyzerAttribute para elegir si el analizador dirige a un idioma o ambos.  Analizadores más sofisticados que requieren modelado detallado del lenguaje sólo pueden tener como destino un solo idioma.  Si el analizador de, por ejemplo, solo comprueba los nombres de tipo o miembro público, es posible usar el modelo de lenguaje común que roslyn ofrece en Visual Basic y C#.  Por ejemplo, FxCop advierte de que una clase implementa <xref:System.Runtime.Serialization.ISerializable>, pero la clase no tiene la <xref:System.SerializableAttribute> atributo es independiente del lenguaje y funciona con código de Visual Basic y C#.

## <a name="initalizing-the-analyzer"></a>Inicializar el analizador

 Desplácese hacia abajo un poco en el `DiagnosticAnalyzer` clase para ver el `Initialize` método.  El compilador llama a este método cuando se activa un analizador.  El método toma un `AnalysisContext` objeto que permite que el analizador que se va a obtener información de contexto como registrar devoluciones de llamada de eventos para los tipos de código que desea analizar.

```csharp
public override void Initialize(AnalysisContext context) {}

```

Abrir una nueva línea en este método y el tipo "contexto". Para ver una lista de finalización de IntelliSense.  Puede ver la lista de finalización hay muchos `Register...` métodos para controlar los distintos tipos de eventos.  Por ejemplo, la primera de ellas, `RegisterCodeBlockAction`, llamadas de vuelta a su código de un bloque, lo que suele ser código entre llaves.  Registrarse para un bloque también vuelve a llamar al código para el inicializador de un campo, el valor dado a un atributo o el valor de un parámetro opcional.

Otro ejemplo sería `RegisterCompilationStartAction`, llamadas de vuelta a su código al principio de una compilación, lo que resulta útil cuando necesite recopilar estado a través de varias ubicaciones.  Puede crear una estructura de datos, por ejemplo, para recopilar todos los símbolos que se utilizan, y cada vez que el analizador se llama atrás para algunas sintaxis o símbolo, puede guardar la información acerca de cada ubicación en la estructura de datos.  Cuando se le llama volver debido a la hora de finalización compilación, puede analizar todas las ubicaciones de guardado, por ejemplo, para informar de los símbolos que se utiliza el código de cada uno `using` instrucción.

Mediante el **sintaxis visualizador**, ha aprendido que desea que se llama cuando el compilador procesa un ObjectCreationExpression.  Use este código para configurar la devolución de llamada:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Registrar para un nodo de la sintaxis y el filtro para solo creación sintaxis los nodos de objeto.  Por convención, los autores de analizador usar una expresión lambda al registrar acciones, lo que ayuda a mantener los analizadores sin estado.  Puede usar la característica de Visual Studio **generar a partir del uso** para crear el `AnalyzeObjectCreation` método.  Esto genera el tipo de parámetro de contexto correcto demasiado.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Establecer las propiedades de los usuarios de su analizador

Para que el analizador aparezca en la interfaz de usuario de Visual Studio correctamente, busque y modifique la siguiente línea de código para identificar el analizador:

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

A continuación busque y abra la `Resources.resx` archivo en el proyecto con el **el Explorador de soluciones**.  Puede colocar en una descripción para el analizador, título, etcetera.  Puede cambiar el valor en todas ellas a `"Don't use ImmutableArray<T> constructor"` por ahora.  Puede colocar la cadena de formato argumentos en la cadena ({0}, {1}, etc.) y versiones posteriores cuando se llama a `Diagnostic.Create()`, puede proporcionar un `params` matriz de argumentos que se pasan.

## <a name="analyzing-an-object-creation-expression"></a>Analizar una expresión de creación de objeto

El `AnalyzeObjectCreation` método toma un tipo diferente de contexto proporcionado por el marco de trabajo del analizador de código.  El método Initialize `AnalysisContext` permite registrar devoluciones de llamada de acción para configurar el analizador.  El `SyntaxNodeAnalysisContext`, por ejemplo, tiene un `CancellationToken` que puedes pasar alrededor.  Si un usuario empieza a escribir en el editor, Roslyn cancelará analizadores de ejecución para guardar el trabajo y mejorar el rendimiento.  Como otro ejemplo, este contexto tiene una propiedad de nodo que devuelve el nodo de sintaxis de creación de objeto.

Obtenga el nodo, que se puede suponer que es el tipo para el que se filtra la acción de nodo de la sintaxis:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Inicie Visual Studio con el analizador de la primera vez

Inicie Visual Studio al compilar y ejecutar el analizador (presione **F5**).  Porque el inicio del proyecto en el **el Explorador de soluciones** es el proyecto VSIX, ejecuta las compilaciones de código el código y una extensión VSIX y, a continuación, inicia Visual Studio con ese VSIX instalado.  Al iniciar Visual Studio de esta manera, se inicia con un subárbol del registro distintos para que su uso principal de Visual Studio no se verán afectado por las instancias de pruebas durante la creación de analizadores.  La primera vez que inicie este modo, Visual Studio realiza varias inicializaciones similares a cuando se inició por primera vez Visual Studio después de instalarlo.

Cree un proyecto de consola y, a continuación, escriba el código de la matriz en el método Main de las aplicaciones de consola:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Las líneas de código con `ImmutableArray` tienen subrayados ondulados porque tiene que obtener el paquete de NuGet inmutable y agregar un `using` instrucción en el código.  Presione el botón derecho del puntero en el nodo de proyecto en el **el Explorador de soluciones** y elija **administrar paquetes de NuGet...** .  En el Administrador de NuGet, escriba "Inmutable" en el cuadro de búsqueda y elija el elemento "System.Collections.Immutable" (no elija "Microsoft.Bcl.Immutable") en el panel izquierdo y presione el botón instalar en el panel derecho.  Instalar el paquete, agrega una referencia a las referencias del proyecto.

Sigue viendo un subrayado ondulado rojo en `ImmutableArray`, coloque el símbolo de intercalación en ese identificador y presione **CTRL +.** (punto) para mostrar el menú de corrección sugerida y optar por agregar adecuado `using` instrucción.

**Guarde y cierre** la segunda instancia de Visual Studio por ahora para ponerte en un estado limpio para continuar.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Finalizar el analizador utilizando Editar y continuar

En la primera instancia de Visual Studio, establezca un punto de interrupción al principio de su `AnalyzeObjectCreation` método presionando **F9** con el símbolo de intercalación en la primera línea.

Iniciar el analizador de nuevo con **F5**y en la segunda instancia de Visual Studio, vuelva a abrir la aplicación de consola que creó la última vez.

Devuelve la primera instancia de Visual Studio en el punto de interrupción porque el compilador Roslyn vio una expresión de creación de objeto y se llama en el analizador.

**Obtiene el nodo de creación de objeto.** Paso a través de la línea que establece el `objectCreation` variable presionando **F10**y en el **ventana Inmediato** evaluar la expresión `"objectCreation.ToString()"`.  Verá que el nodo de sintaxis la variable apunta a es el código `"new ImmutableArray<int>()"`, simplemente lo está buscando.

**Obtener ImmutableArray < T\> objeto de tipo.** Deberá comprobar si el tipo que se va a crear es ImmutableArray.  En primer lugar, obtenga el objeto que representa este tipo.  Comprobar tipos mediante el modelo semántico para asegurarse de tiene exactamente el tipo correcto y no compara la cadena de ToString().  Escriba la siguiente línea de código al final de la función:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Designar tipos genéricos en metadatos con backquotes (') y el número de parámetros genéricos.  Por este motivo, no ve "... ImmutableArray\<T > "en el nombre de metadatos.

El modelo semántico tiene muchas cosas útiles que le permiten formular preguntas acerca de los símbolos, flujo de datos, duración de la variable, etcetera.  Roslyn separa los nodos de la sintaxis del modelo semántico por distintas razones ingeniería (rendimiento, modelado código erróneo, etcetera.).  Desea que el modelo de compilación que se buscará información contenida en las referencias para la comparación exacta.

Puede arrastrar el puntero de ejecución amarillo en el lado izquierdo de la ventana del editor.  Arrástrela hasta la línea que establece el `objectCreation` variable y paso a través de la nueva línea de código mediante **F10**.  Si sitúa el puntero del mouse sobre la variable `immutableArrayOfType`, verá que se encuentra el tipo exacto en el modelo semántico.

**Obtiene el tipo de la expresión de creación de objeto.** "Tipo" se utiliza en varias maneras en este artículo, pero esto significa que si tiene "Foo nuevo" expresión, tendrá que obtener un modelo de Foo.  Tendrá que obtener el tipo de la expresión de creación de objetos para ver si es el ImmutableArray\<T > tipo.  Utilice el modelo semántico de nuevo para obtener información de símbolos para el símbolo de tipo (ImmutableArray) en la expresión de creación de objeto.  Escriba la siguiente línea de código al final de la función:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Dado que el analizador debe controlar el código incompleto o incorrecto en búferes de editor (por ejemplo, hay una falta `using` instrucción), debe comprobar si hay `symbolInfo` que se va a `null`.  Debe obtener un tipo con nombre (INamedTypeSymbol) desde el objeto de información de símbolos para finalizar el análisis.

**Comparar los tipos.** Dado que hay un tipo genérico abierto de T que estamos buscando, y el tipo en el código es un tipo genérico concreto, consultar la información de símbolos para el tipo de qué se construye a partir (un tipo genérico abierto) y compara ese resultado con `immutableArrayOfTType`.  Escriba lo siguiente al final del método:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Notificar el diagnóstico.** Informes de diagnóstico es bastante fácil.  Utilice la regla creada automáticamente en la plantilla de proyecto, que se define antes del método de inicialización.  Dado que esta situación en el código es un error, puede cambiar la línea que inicializa la regla para reemplazar `DiagnosticSeverity.Warning` (subrayado ondulado de color verde) con `DiagnosticSeverity.Error` (subrayado ondulado de color rojo).  El resto de la regla se inicializa desde los recursos que edita cerca del principio del tutorial.  También debe informar de la ubicación de las marcas en zigzag, que es la ubicación de la especificación de tipo de la expresión creación de objeto.  Escriba este código en el `if` bloque:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La función debe ser similar al siguiente (que quizás un formato diferente):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Quite el punto de interrupción para que pueda ver el trabajo del analizador (y dejar de devolver a la primera instancia de Visual Studio).  Arrastre el puntero de ejecución al principio del método y presione **F5** para continuar con la ejecución.  Cuando se cambia a la segunda instancia de Visual Studio, el compilador se iniciará examinar el código nuevo y lo llamará en el analizador.  Puede ver un subrayado ondulado bajo `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Agregar una "revisión de código" para el problema de código

Antes de comenzar, cierre la segunda instancia de Visual Studio y detener la depuración en la primera instancia de Visual Studio (donde está desarrollando el analizador).

**Agregue una nueva clase.** Use el menú contextual (botón derecho del puntero) en el nodo del proyecto en el Explorador de soluciones y elija Agregar un nuevo elemento.  Agregue una clase denominada `BuildCodeFixProvider`.  Esta clase debe derivarse de `CodeFixProvider`, y deberá usar **CTRL +.** (punto) para invocar la corrección del código que agrega el valor correcto `using` instrucción.  Esta clase también debe anotarse con `ExportCodeFixProvider` atributo y será necesario agregar un `using` instrucción que se va a resolver el `LanguageNames` enum.  Debe tener un archivo de clase con el siguiente código en él:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Código auxiliar de los miembros derivados.** Ahora, colocar el símbolo de intercalación del editor en el identificador `CodeFixProvider` y presione **CTRL +.** (punto) para la implementación para esta clase base abstracta de código auxiliar.  Esto genera una propiedad y un método.

**Implementa la propiedad.** Rellene la `FixableDiagnosticIds` la propiedad `get` cuerpo con el código siguiente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn reúne diagnósticos y corrige comparando estos identificadores, que son simplemente cadenas.  La plantilla de proyecto genera un identificador de diagnóstico, y está disponible cambiarlo.  El código de la propiedad sólo devuelve el identificador de la clase de analizador.

**El método RegisterCodeFixAsync toma un contexto.** El contexto es importante porque puede aplicar una revisión de código para varios diagnósticos o podría haber más de un problema en una línea de código.  Si escribe "contexto". en el cuerpo del método, la lista de finalización de IntelliSense le mostrará a algunos miembros útiles.  Hay un miembro de CancellationToken que puede comprobar para ver si algo quiere cancelar la corrección.  Hay un miembro de documento que tiene un gran número de miembros útiles y le permite llegar a los objetos de modelo de proyecto y solución.  Hay un miembro de intervalo que es el inicio y final de la ubicación del código especifica cuándo se notifica el diagnóstico.

**Convierta el método ser asincrónico.** Lo primero que debe hacer es corregir la declaración del método generado para que sea un `async` método.  La corrección del código de procesamiento con stubs de la implementación de una clase abstracta no incluye el `async` palabra clave incluso aunque el método devuelve un `Task`.

**Obtener la raíz del árbol de sintaxis.** Para modificar el código que necesita para generar un nuevo árbol de sintaxis con los cambios se realiza la corrección del código.  Necesita la `Document` desde el contexto para llamar a `GetSyntaxRootAsync`.  Se trata de un método asincrónico porque hay trabajo desconocido que se va a obtener del árbol de sintaxis, posiblemente como obtener el archivo de disco, analizarlo y generar el modelo de código de Roslyn para él.  La interfaz de usuario de Visual Studio debe responder durante este tiempo, donde el uso `async` permite.  Reemplace la línea de código en el método por el siguiente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Busque el nodo con el problema.** Pasar en el intervalo del contexto, pero el nodo que buscar no sea el código que se debe cambiar.  El diagnóstico incluido solo ofrece el intervalo para el identificador de tipo (donde las marcas en zigzag pertenecían), pero es necesario reemplazar la expresión de creación de objetos completo, incluido el `new` palabra clave al principio y los paréntesis al final.  Agregue el código siguiente al método (y usar **CTRL +.** Para agregar una `using` instrucción para `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrar la corrección del código para la interfaz de usuario de bombilla.** Al registrar la corrección del código, Roslyn se conecta automáticamente a la interfaz de usuario de Visual Studio una bombilla.  Los usuarios finales verán pueden usar **CTRL +.** (punto) cuando el analizador de líneas en zigzag una mala `ImmutableArray<T>` uso del constructor.  Dado que el proveedor de la revisión de código solo se ejecuta cuando se produce un problema, puede asumir que tiene la expresión de creación de objeto que buscaba.  El parámetro de contexto, puede registrar la nueva revisión de código agregando el código siguiente al final de `RegisterCodeFixAsync` método:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Debe colocar el símbolo de intercalación del editor en el identificador, `CodeAction`, a continuación, utilice **CTRL +.** (punto) para agregar la correspondiente `using` instrucción para este tipo.

A continuación, colocar el símbolo de intercalación del editor en el `ChangeToImmutableArrayEmpty` identificador y el uso **CTRL +.** para generar este código auxiliar del método.

Este último fragmento de código que agregó registra la corrección del código, pasando una `CodeAction` y el identificador de diagnóstico para el tipo de problema encontrado.  En este ejemplo, solo hay un Id. de diagnóstico que este código proporciona correcciones para, por lo que solo se puede pasar el primer elemento de la matriz de identificadores de diagnóstico.  Cuando se crea el `CodeAction`, se pasa en el texto que debe usar la interfaz de usuario de una bombilla como una descripción de la revisión de código.  También se pasa una función que toma un objeto CancellationToken y devuelve un nuevo documento.  El nuevo documento tiene un nuevo árbol de sintaxis que incluye el código revisado que llama `ImmutableArray.Empty`.  Este fragmento de código utiliza una expresión lambda para que puede cerrar sobre el nodo objectCreation y documento del contexto.

**Construir el nuevo árbol de sintaxis.** En el `ChangeToImmutableArrayEmpty` método cuyo código auxiliar que ha generado anteriormente, escriba la línea de código: `ImmutableArray<int>.Empty;`.  Si ve la ventana de herramientas del visualizador de sintaxis de nuevo, puede ver que esta sintaxis es un nodo SimpleMemberAccessExpression.  Es lo que este método se debe construir y devolver en un nuevo documento.

El primer cambio que `ChangeToImmutableArrayEmpty` consiste en agregar `async` antes de `Task<Document>` porque los generadores de código no se pueden suponer que el método debe ser asincrónico.

Rellene el cuerpo con el código siguiente para que el método tiene un aspecto similar al siguiente:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Debe colocar el símbolo de intercalación del editor en el `SyntaxGenerator` identificador y el uso **CTRL +.** (punto) para agregar la correspondiente `using` instrucción para este tipo.

Este código usa `SyntaxGenerator`, que es un tipo muy útil para crear código nuevo.  Después de obtener un generador para el documento que tiene el problema de código, `ChangeToImmutableArrayEmpty` llamadas `MemberAccessExpression`, pasando el tipo que tiene el miembro que desea obtener acceso y pasando el nombre del miembro como una cadena.

A continuación, el método de captura la raíz del documento, y dado que esto puede implicar trabajo arbitraria por lo general, el código espera esta llamada y pasa el token de cancelación.  Modelos de código de Roslyn son inmutables, similar a trabajar con una cadena. NET; al actualizar la cadena, obtendrá un nuevo objeto de cadena de vuelta.  Cuando se llama a `ReplaceNode`, se recibe un nuevo nodo raíz.  La mayor parte del árbol de sintaxis se comparta (dado que es inmutable), pero la `objectCreation` nodo se sustituye por la `memberAccess` nodo, así como todos los nodos primarios hasta la raíz del árbol de sintaxis.

## <a name="trying-your-code-fix"></a>Tratar la corrección del código

Ahora puede presionar **F5** para ejecutar el analizador en una segunda instancia de Visual Studio.  Abra el proyecto de consola que usó antes.  Ahora debería aparecer la bombilla donde es la expresión de creación de objeto nuevo para `ImmutableArray<int>`.  Si presiona **CTRL +.** (punto), a continuación, verá el código corregir, y verá una vista previa de diferencia de código generado automáticamente en la interfaz de usuario de bombilla.  Roslyn Esto crea automáticamente.

**Sugerencias de Pro:** si iniciar la segunda instancia de Visual Studio y no ve la bombilla con la corrección del código, debe borrar la caché de componentes de Visual Studio.  Borrar la memoria caché fuerza a Visual Studio para volver a examinar los componentes, por lo que, a continuación, Visual Studio debe recoger el componente más reciente.  En primer lugar, cierre la segunda instancia de Visual Studio.  A continuación, en el Explorador de Windows, vaya al directorio del usuario (c:\users\\< userid\>) y busque AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  En este directorio, elimine el directorio de sub ComponentModelCache.  Los cambios "14" versiones con Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Charla de vídeo y proyectos de código de la fecha de fin

Puede ver en este ejemplo, desarrollan y se describe más adelante en [esta charla](http://channel9.msdn.com/events/Build/2015/3-725).  Hablar muestra el analizador de trabajo y le guía a través de compilarlas.

Puede ver todo el código termine [aquí](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Las subcarpetas DoNotUseImmutableArrayCollectionInitializer y DoNotUseImmutableArrayCtor tienen un archivo de C# para buscar problemas y un archivo de C# que implementa las correcciones de código que se muestran en la interfaz de usuario de Visual Studio una bombilla.  Tenga en cuenta que el código final tiene un poco más abstracción para evitar obtener lo ImmutableArray\<T > tipo object una y otra vez.  Realiza las acciones registradas anidadas para guardar el objeto de tipo en un contexto que está disponible siempre que las acciones de sub (analizar la creación de objetos y analizar las inicializaciones de colección) ejecutar.

## <a name="see-also"></a>Vea también

* [\\Charla de \build 2015](http://channel9.msdn.com/events/Build/2015/3-725)
* [Código completo en GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Varios ejemplos en GitHub, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Otros documentos en el sitio de GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Reglas de FxCop implementadas con analizadores de Roslyn en GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
