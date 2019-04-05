---
title: Analizadores de Roslyn y biblioteca compatible con el código para ImmutableArrays | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c15b1f335129e7c749aadefaa78ee3f9c5862baa
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "59002236"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizadores de Roslyn y biblioteca compatible con código para ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") le ayuda a crear bibliotecas de código. Una biblioteca de código proporciona funcionalidad que puede usar y (analizadores de Roslyn) de las herramientas que le ayudarán a usar la biblioteca de la mejor manera o para evitar errores. Este tema muestra cómo crear un analizador de Roslyn del mundo real para detectar errores comunes al usar el [NIB: Las colecciones inmutables](http://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) paquete NuGet. El ejemplo también muestra cómo proporcionar una corrección de código para un problema de código encontrado por el analizador. Los usuarios ver las correcciones de código en la bombilla de Visual Studio la interfaz de usuario y pueden aplicar una revisión para el código automáticamente.

## <a name="getting-started"></a>Introducción
Necesita lo siguiente para compilar este ejemplo:

- Visual Studio 2015 (no una edición Express) o una versión posterior. Puede usar gratuitamente el [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). También puede, al instalar Visual Studio, comprobar herramientas de extensibilidad de Visual Studio en herramientas comunes para instalar el SDK al mismo tiempo. Si ya ha instalado Visual Studio, también puede instalar este SDK, vaya al menú principal **archivo &#124; New &#124;proyecto...** , elija C# en el panel de navegación izquierdo y, a continuación, elija extensibilidad. Cuando se elige el "**instalar las herramientas de extensibilidad de Visual Studio**" plantilla de proyecto de la ruta de navegación, le pedirá que descargue e instale el SDK.

- [.NET compiler Platform («Roslyn») SDK](https://aka.ms/roslynsdktemplates). También puede instalar este SDK, vaya al menú principal **archivo &#124; New &#124; proyecto...** , elegir **C#** en el panel de navegación izquierdo y, después, elige **extensibilidad**. Al elegir "**descargar el SDK de .NET Compiler Platform**" plantilla de proyecto de la ruta de navegación, le pedirá que descargue e instale el SDK. Este SDK incluye la [visualizador de sintaxis Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Esta herramienta muy útil le ayuda a descubrir qué tipos de modelo de código que debe buscar en el analizador. Las llamadas de la infraestructura de analizador en el código para los tipos de modelo de código específico, por lo que el código solo se ejecuta cuando sea necesario y puede centrarse solo en el análisis de código relevante.

## <a name="whats-the-problem"></a>¿Cuál es el problema?
Imagine que proporcionar una biblioteca con ImmutableArray (por ejemplo, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) admite. Los desarrolladores de C# tienen mucha experiencia con las matrices. NET. Sin embargo, debido a la naturaleza de las técnicas de optimización y ImmutableArrays que se utiliza en la implementación, intuitions para desarrolladores de C# que los usuarios de la biblioteca escribir código roto, tal como se explica más adelante. Además, los usuarios no ven sus errores hasta el tiempo de ejecución, lo que no se usan en Visual Studio con .NET para la experiencia de calidad.

Los usuarios están familiarizados con la escritura de código similar al siguiente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Creación de matrices vacías a rellenar con las siguientes líneas de código y el uso de sintaxis de inicializador de colección son muy familiares para los desarrolladores de C#. Sin embargo, escribir el mismo código para una matriz ImmutableArray se bloquea en tiempo de ejecución:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

El primer error es debido a la implementación de ImmutableArray mediante un struct para ajustar el almacenamiento de datos subyacente. Las estructuras deben tener constructores sin parámetros para que `default(T)` expresiones pueden devolver structs con todos cero o nulos miembros. Cuando el código tiene acceso a `b1.Length`, hay un valor null de tiempo de ejecución desreferenciar error porque no hay ninguna matriz de almacenamiento subyacente de la estructura ImmutableArray. La manera correcta para crear una matriz ImmutableArray vacía es `ImmutableArray<int>.Empty`.

 Se produce el error con inicializadores de colección porque el método ImmutableArray.Add devuelve nuevas instancias cada vez que lo llama. Dado que ImmutableArrays nunca cambian, cuando se agrega un nuevo elemento, obtendrá un nuevo objeto ImmutableArray (que puede compartir el almacenamiento por motivos de rendimiento con una ImmutableArray previamente existente). Dado que `b2` apunta a la primera ImmutableArray antes de llamar a `Add()` cinco veces, `b2` es un valor predeterminado ImmutableArray. Error de desreferenciación de llamar a longitud en él también se bloquea con un valor null. La manera correcta de inicializar una matriz ImmutableArray sin llamar manualmente a agregar es usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Buscar tipos de nodo de sintaxis relevantes para desencadenar el analizador
Para empezar a compilar el analizador, en primer lugar averiguar qué tipo de elemento SyntaxNode que necesitará buscar.   Iniciar el visualizador de sintaxis en el menú **vista &#124; Other Windows &#124; visualizador de sintaxis Roslyn**.

Coloque el símbolo de intercalación del editor en la línea que declara `b1`. Verá el visualizador de sintaxis muestra que se encuentra en un `LocalDeclarationStatement` nodo del árbol de sintaxis. Este nodo tiene un `VariableDeclaration`, que a su vez tiene una `VariableDeclarator`, que a su vez tiene una `EqualsValueClause`y, por último, hay un `ObjectCreationExpression`. Al hacer clic en el árbol del visualizador de sintaxis de nodos, la sintaxis en la ventana del editor se resaltan para mostrar el código representado por ese nodo. Los nombres de los tipos de sub SyntaxNode coinciden con los nombres utilizados en la gramática de C#.

## <a name="creating-the-analyzer-project"></a>Crear el proyecto de analizador
En el menú principal, elija **archivo &#124; New &#124; proyecto...** . En el **nuevo proyecto** cuadro de diálogo, en **C#** proyectos en la barra de navegación izquierdo, elija la extensibilidad y en el panel derecho, elija el **analizador con corrección de código** proyecto plantilla. Escriba un nombre y confirme el cuadro de diálogo.

La plantilla abre un archivo DiagnosticAnalyzer.cs. Seleccione a ese editor ficha de búfer. Este archivo tiene una clase del analizador (tiene el formato del nombre que dio al proyecto) que se deriva de `DiagnosticAnalyzer` (un tipo de API de Roslyn). La nueva clase tiene un `DiagnosticAnalyzerAttribute` declarar su analizador es relevante para el lenguaje C# para que el compilador detecta y carga el analizador.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Puede implementar un analizador mediante Visual Basic que tiene como destino el código de C#, y viceversa. Es más importante en el DiagnosticAnalyzerAttribute para elegir si el analizador tiene como destino un idioma o ambos. Los analizadores más sofisticados que requieren modelado detallado del lenguaje solo pueden tener como destino un único idioma. Si el analizador, por ejemplo, solo comprueba los nombres de tipo o los nombres de miembro público, es posible usar el modelo de lenguaje común que roslyn ofrece a través de Visual Basic y C#. Por ejemplo, FxCop advierte de que una clase implementa <xref:System.Runtime.Serialization.ISerializable>, pero la clase no tiene el <xref:System.SerializableAttribute> atributo es independiente del lenguaje y funciona con código de Visual Basic y C#.

## <a name="initalizing-the-analyzer"></a>Inicializar el analizador
Desplácese hacia abajo un poco en el `DiagnosticAnalyzer` clase para ver el `Initialize` método. El compilador llama a este método cuando se activa un analizador. El método toma un `AnalysisContext` objeto que permite que el analizador para obtener información de contexto y registrar devoluciones de llamada para los eventos para los tipos de código que desea analizar.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Abra una nueva línea en este método y el tipo "contexto". Para ver una lista de finalización de Intellisense. Puede ver en la lista de finalización hay muchos `Register…` métodos para controlar distintos tipos de eventos. Por ejemplo, la primera de ellas, `RegisterCodeBlockAction`, llamadas de vuelta a su código para un bloque, que suele ser código entre llaves. Registrarse para un bloque también vuelve a llamar al código para el inicializador de campo, el valor dado a un atributo o el valor de un parámetro opcional.

Otro ejemplo sería `RegisterCompilationStartAction`, llamadas de vuelta a su código al principio de una compilación, lo que resulta útil cuando tiene que recopilar estado a través de varias ubicaciones. Puede crear una estructura de datos, por ejemplo, para recopilar todos los símbolos que se utiliza, y cada vez que el analizador se llama a algún sintaxis o un símbolo, puede guardar información acerca de cada ubicación en la estructura de datos. Cuando se llama a atrás debido a una finalización de la compilación, puede analizar todas las ubicaciones de guardado, por ejemplo, para informar de los símbolos que se usa el código de cada `using` instrucción.

Mediante el **visualizador de sintaxis**, ha aprendido que desea que se llama cuando el compilador procesa un ObjectCreationExpression. Use este código para configurar la devolución de llamada:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Registrar para un nodo de sintaxis y el filtro para los nodos de sintaxis de creación a solo objeto. Por convención, los autores de analyzer usar una expresión lambda al registrar acciones, que ayuda a mantener los analizadores sin estado. Puede usar la característica de Visual Studio **Generate From Usage** para crear el `AnalyzeObjectCreation` método. Esto genera el tipo de parámetro de contexto correcto de demasiado.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Establecer las propiedades de los usuarios de su analizador
Para que el analizador se muestra en la interfaz de usuario de Visual Studio correctamente, busque y modifique la siguiente línea de código para identificar el analizador:

```csharp
internal const string Category = "Naming";
```

Cambio `"Naming"` a `"API Guidance"`.

A continuación busque y abra el archivo Resources.resx en el proyecto con el **el Explorador de soluciones**. Puede colocar en una descripción para el analizador, título, etcetera. Puede cambiar el valor para todos ellos a `“Don’t use ImmutableArray<T> constructor”` por ahora. Puede colocar los argumentos de la cadena de formato de cadena ({0}, {1}, etc.) y versiones posteriores al llamar a `Diagnostic.Create()`, puede proporcionar una matriz de parámetros de argumentos que deben pasarse.

## <a name="analyzing-an-object-creation-expression"></a>Analizar una expresión de creación de objeto
El `AnalyzeObjectCreation` método toma un tipo diferente de contexto proporcionado por el marco de trabajo del analizador de código. El método Initialize `AnalysisContext` le permite registrar devoluciones de llamada de acción para configurar el analizador. El `SyntaxNodeAnalysisContext`, por ejemplo, tiene un `CancellationToken` que puede pasar. Si un usuario empieza a escribir en el editor, Roslyn cancelará la ejecución analizadores para guardar el trabajo y mejorar el rendimiento. Como otro ejemplo, este contexto tiene una propiedad de nodo que devuelve el nodo de sintaxis de creación de objeto.

Obtenga el nodo que se puede suponer que es el tipo para el que se filtra la acción de nodo de sintaxis:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Inicie Visual Studio con el analizador de la primera vez
Inicie Visual Studio al compilar y ejecutar el analizador (presione **F5**). Dado que el inicio del proyecto en el **el Explorador de soluciones** es el proyecto VSIX, que ejecutan las compilaciones de código del código y una extensión VSIX y, a continuación, se inicia Visual Studio con ese VSIX instalada. Al iniciar Visual Studio de este modo, se inicia con un subárbol del registro distinto para que su uso principal de Visual Studio no se verán afectado por las instancias de pruebas durante la compilación de los analizadores. La primera vez que inicie esta forma, Visual Studio realiza las inicializaciones varias similares a cuando se inició por primera vez Visual Studio después de instalarlo.

 Cree un proyecto de consola y, a continuación, escriba el código de la matriz en el método Main de las aplicaciones de consola:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Las líneas de código con `ImmutableArray` tienen subrayados ondulados porque la necesitará obtener el paquete NuGet inmutable y agregar un `using` instrucción en el código. Presione el botón derecho del puntero en el nodo del proyecto en el **el Explorador de soluciones** y elija **administrar paquetes NuGet...** . En el Administrador de NuGet, escriba "Inmutable" en el cuadro de búsqueda y elija el elemento "System.Collections.Immutable" (no elija "Microsoft.Bcl.Immutable") en el panel izquierdo y presione el botón instalar en el panel derecho. Instalar el paquete, agrega una referencia a las referencias del proyecto.

Aún aparece un subrayado ondulado rojo debajo de `ImmutableArray`, coloque el símbolo de intercalación en ese identificador y presione **CTRL +.** (punto) para mostrar el menú de la corrección sugerida y optar por agregar adecuado `using` instrucción.

**Guarde y cierre** la segunda instancia de Visual Studio por ahora para ponerle en un estado limpio para continuar.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Finalizando el analizador utilizando Editar y continuar
En la primera instancia de Visual Studio, establezca un punto de interrupción al principio de su `AnalyzeObjectCreation` método presionando **F9** con el símbolo de intercalación en la primera línea.

Inicie el analizador de nuevo con **F5**y en la segunda instancia de Visual Studio, vuelva a abrir la aplicación de consola que creó la última vez.

Volver a la primera instancia de Visual Studio en el punto de interrupción porque el compilador Roslyn vio una expresión de creación de objeto y llama en el analizador.

**Obtiene el nodo de creación del objeto.** Paso a través de la línea que establece el `objectCreation` variable presionando **F10**y en el **ventana Inmediato** evaluar la expresión `“objectCreation.ToString()”`. Verá que el nodo de sintaxis, la variable apunta a es el código `"new ImmutableArray<int>()"`, simplemente lo busca.

**Obtener ImmutableArray\<T > objeto de tipo.** Deberá comprobar si el tipo que se va a crear es ImmutableArray. En primer lugar, obtenga el objeto que representa este tipo. Compruebe los tipos mediante el modelo semántico para asegurarse de tiene exactamente el tipo correcto y no compara la cadena de ToString(). Escriba la siguiente línea de código al final de la función:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Designar tipos genéricos en los metadatos con backquotes (') y el número de parámetros genéricos. Por este motivo, no ve "... ImmutableArray\<T > "en el nombre de metadatos.

El modelo semántico tiene muchas cosas útiles que le permiten formular preguntas acerca de los símbolos, flujo de datos, duración de la variable, etcetera. Roslyn separa los nodos de sintaxis del modelo semántico por diversos motivos engineering (rendimiento, modelado de código erróneo, etcetera.). Desea que el modelo de compilación para buscar información contenida en las referencias para la comparación preciso.

Puede arrastrar el puntero de ejecución amarillo en el lado izquierdo de la ventana del editor. Arrástrela hasta la línea que establece el `objectCreation` variable y paso a través de la nueva línea de código mediante **F10**. Si mantiene el puntero del mouse sobre la variable `immutableArrayOfType`, verá que se encuentra el tipo exacto en el modelo semántico.

**Obtiene el tipo de expresión de creación de objeto.** "Type" se utiliza en algunas formas en este artículo, pero esto significa que si tiene "Foo nuevo" expresión, deberá obtener un modelo de Foo. Deberá obtener el tipo de la expresión de creación de objetos para ver si es ImmutableArray\<T > tipo. Utilice el modelo semántico de nuevo para obtener información de símbolos para el tipo de símbolo (ImmutableArray) en la expresión de creación de objeto. Escriba la siguiente línea de código al final de la función:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Dado que el analizador debe controlar código incompleto o incorrecto de los búferes del editor (por ejemplo, hay una falta `using` instrucción), debe comprobar si hay `symbolInfo` que se va a `null`. Deberá obtener un tipo con nombre (INamedTypeSymbol) desde el objeto de información de símbolos para finalizar el análisis.

**Compare los tipos.** Dado que hay un tipo genérico abierto de T que estamos buscando y el tipo en el código es un tipo genérico concreto, consultar la información de símbolos para el tipo de qué se construye a partir (un tipo genérico abierto) y compara ese resultado con `immutableArrayOfTType`. Escriba lo siguiente al final del método:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Notificar el diagnóstico.** El diagnóstico de informes es bastante fácil. Utilice la regla que se crea en la plantilla de proyecto, que se define antes del método Initialize. Dado que esta situación en el código es un error, puede cambiar la línea que inicializa la regla para reemplazar `DiagnosticSeverity.Warning` (subrayado ondulado de color verde) con `DiagnosticSeverity.Error` (subrayado ondulado de color rojo). Inicializa el resto de la regla de los recursos que puede editar al principio del tutorial. También deberá informar de la ubicación de la línea ondulada, que es la ubicación de la especificación del tipo de expresión de creación de objeto. Escriba este código en el `if` bloque:

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
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Quite el punto de interrupción para que pueda ver su funcionamiento del analizador (y dejar de devolver a la primera instancia de Visual Studio). Arrastre el puntero de ejecución al principio del método y presione **F5** para continuar la ejecución. Al cambiar a la segunda instancia de Visual Studio, se iniciará el compilador examinar el código nuevo y lo llamará en el analizador. Puede ver un subrayado ondulado bajo `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Adición de una "corrección de código" para el problema de código
Antes de comenzar, cierre la segunda instancia de Visual Studio y detener la depuración en la primera instancia de Visual Studio (donde está desarrollando el analizador).

**Agregue una nueva clase.** Use el menú contextual (botón derecho del puntero) en el nodo del proyecto en el Explorador de soluciones y elija Agregar un nuevo elemento. Agregue una clase denominada `BuildCodeFixProvider`. Esta clase debe derivarse de `CodeFixProvider`, y deberá usar **CTRL +.** (punto) para invocar la corrección de código que agrega el valor correcto `using` instrucción. Esta clase también debe anotarse con `ExportCodeFixProvider` atributo y será necesario agregar un `using` instrucción para resolver el `LanguageNames` enum. Debe tener un archivo de clase con el código siguiente en él:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Código auxiliar de los miembros derivados.** Ahora, coloque de intercalación del símbolo en el identificador `CodeFixProvider` y presione **CTRL +.** (punto) para la implementación de esta clase base abstracta de código auxiliar. Esto genera una propiedad y un método.

**Implemente la propiedad.** Rellene el `FixableDiagnosticIds` la propiedad `get` cuerpo con el código siguiente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn reúne los diagnósticos y correcciones mediante la coincidencia de estos identificadores, que son simplemente cadenas. La plantilla de proyecto genera un Id. de diagnóstico, y puede cambiarla. El código de la propiedad sólo devuelve el identificador de la clase del analizador.

**El método RegisterCodeFixAsync toma un contexto.** El contexto es importante porque puede aplicar una corrección de código para varios diagnósticos, o podría haber más de un problema en una línea de código. Si escribe "contexto". en el cuerpo del método, la lista de finalización de Intellisense mostrará a algunos miembros útiles. Hay un miembro de CancellationToken que puede comprobar para ver si algo desea cancelar la corrección. Hay un miembro de documento que tiene una gran cantidad de miembros útiles y le permite llegar a los objetos del modelo de proyecto y solución. Hay un miembro de intervalo que es el inicio y final de la ubicación del código especifica cuándo se notifica el diagnóstico.

**Hacer que el método sean asincrónicos.** Lo primero que necesita hacer es corregir la declaración del método generado para que sea un `async` método. La corrección de código para el procesamiento con stubs de la implementación de una clase abstracta no incluye el `async` palabra clave incluso después de que el método devuelve un `Task`.

**Obtener la raíz del árbol de sintaxis.** Para modificar el código que necesita para generar un nuevo árbol de sintaxis con los cambios se realiza la corrección de código. Necesita el `Document` desde el contexto para llamar a `GetSyntaxRootAsync`. Se trata de un método asincrónico porque hay trabajo desconocido para obtener el árbol de sintaxis, incluida posiblemente obtener el archivo de disco, analizarla y generar el modelo de código de Roslyn para él. La IU de Visual Studio debe ser dinámico durante este tiempo, donde el uso `async` permite. Reemplace la línea de código en el método por el siguiente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Busque el nodo con el problema.** Pasar en el intervalo del contexto, pero el nodo que buscar no sea el código que se debe cambiar. El diagnóstico notificado solo proporciona el intervalo para el identificador del tipo (que pertenecía el subrayado ondulado de color), pero es necesario reemplazar la expresión de creación de objetos completo, incluido el `new` keywoard al principio y los paréntesis al final. Agregue el código siguiente al método (y usar **CTRL +.** Para agregar un `using` instrucción para `ObjectCreationExpressionSyntax`):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Registre la corrección de código para la interfaz de usuario de bombilla.** Al registrar la corrección de código, Roslyn se conecta automáticamente a la bombilla de Visual Studio la interfaz de usuario. Los usuarios finales verán que se pueden usar **CTRL +.** (punto) cuando el analizador de líneas en zigzag una incorrecta `ImmutableArray<T>` uso del constructor. Dado que el proveedor de corrección de código se ejecuta solo cuando hay un problema, puede asumir que tiene la expresión de creación de objeto que estaba buscando. Desde el parámetro de contexto, puede registrar la nueva corrección de código, agregue el código siguiente al final de `RegisterCodeFixAsync` método:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Deberá colocar el símbolo de intercalación del editor en el identificador, `CodeAction`, a continuación, usar **CTRL +.** (punto) para agregar adecuado `using` instrucción para este tipo.

A continuación, colocar el símbolo de intercalación del editor en el `ChangeToImmutableArrayEmpty` identificador y uso **CTRL +.** para generar este código auxiliar del método.

Este último fragmento de código que agregó registra la corrección de código, pasando un `CodeAction` y el Id. de diagnóstico para el tipo de problema encontrado. En este ejemplo, hay solo un Id. de diagnóstico que este código proporciona correcciones para, por lo que puede pasar simplemente el primer elemento de la matriz de identificadores de diagnóstico. Cuando se crea el `CodeAction`, pasa el texto que se debe usar la interfaz de usuario de bombilla como una descripción de la corrección de código. También pasa una función que toma un CancellationToken y devuelve un nuevo documento. El nuevo documento tiene un nuevo árbol de sintaxis que incluye el código revisado que llama a `ImmutableArray.Empty`. Este fragmento de código utiliza una expresión lambda para que pueden cerrar el nodo objectCreation y documento del contexto.

**Construir el nuevo árbol de sintaxis.** En el `ChangeToImmutableArrayEmpty` método cuyo código auxiliar que se ha generado anteriormente, escriba la línea de código: `ImmutableArray<int>.Empty;`. Si ve la ventana de herramientas visualizador de sintaxis de nuevo, puede ver que esta sintaxis es un nodo SimpleMemberAccessExpression. Eso es lo que este método debe construir y devolver un nuevo documento.

El primer cambio en `ChangeToImmutableArrayEmpty` consiste en agregar `async` antes `Task<Document>` porque los generadores de código no se pueden suponer que el método debe ser asincrónico.

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

Deberá colocar el símbolo de intercalación del editor en el `SyntaxGenerator` identificador y uso **CTRL +.** (punto) para agregar adecuado `using` instrucción para este tipo.

Este código usa `SyntaxGenerator`, que es un tipo muy útil para construir el nuevo código. Después de obtener un generador para el documento que tiene el problema de código, `ChangeToImmutableArrayEmpty` llamadas `MemberAccessExpression`, pasando el tipo que tiene el miembro que desea obtener acceso y pasando el nombre del miembro como una cadena.

A continuación, el método captura la raíz del documento, y dado que esto puede implicar trabajo arbitrario en el caso general, el código espera esta llamada y pasa el token de cancelación. Los modelos de código Roslyn son inmutables, similar a trabajar con una cadena. NET; al actualizar la cadena, obtendrá un nuevo objeto de cadena de vuelta. Cuando se llama a `ReplaceNode`, obtendrá un nuevo nodo raíz. Se comparte la mayor parte del árbol de sintaxis (porque es inmutable), pero la `objectCreation` nodo se reemplaza por la `memberAccess` nodo, así como todos los nodos primarios hasta la raíz del árbol de sintaxis.

## <a name="trying-your-code-fix"></a>Probar la corrección de código
Ahora puede presionar **F5** para ejecutar el analizador en una segunda instancia de Visual Studio. Abra el proyecto de consola que usó antes. Ahora debería ver aparecer donde es la expresión de creación de objeto nuevo para la bombilla `ImmutableArray<int>`. Si presiona **CTRL +.** (punto), a continuación, verá el código de corregir, y verá una vista previa de diferencia de código generado automáticamente en la interfaz de usuario de bombilla. Roslyn crea para usted.

Sugerencia de Pro: Si inicia la segunda instancia de Visual Studio y no ve la luz con la corrección de código, es posible que deba borrar la caché de componentes de Visual Studio. Borrar la memoria caché, se fuerza a Visual Studio para volver a examinar los componentes, por lo que, a continuación, Visual Studio debe recoger el componente más reciente. En primer lugar, cierre la segunda instancia de Visual Studio. A continuación, en el Explorador de Windows, vaya al directorio del usuario (c:\users\\< userid\>) y busque AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\. En este directorio, elimine el directorio de sub ComponentModelCache. El "14" cambia una versión a otra con Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Vídeo de charla y proyectos de código de la fecha de fin
Puede ver este ejemplo desarrollado y se describe con más detalle en [esta charla](http://channel9.msdn.com/events/Build/2015/3-725). La charla muestra el analizador de trabajo y le guiará a través de crearlo.

Puede ver todo el código terminado [aquí](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Las subcarpetas DoNotUseImmutableArrayCollectionInitializer y DoNotUseImmutableArrayCtor tienen un archivo de C# para buscar problemas y un archivo de C# que implementa las correcciones de código que se muestran en la bombilla de Visual Studio la interfaz de usuario. Tenga en cuenta, el código terminado un poco más de abstracción para evitar capturar ImmutableArray\<T > tipo de objeto y otra vez. Usa anidada las acciones registradas para guardar el objeto de tipo en un contexto que está disponible cada vez que las acciones de sub (analizar la creación de objetos y analizar las inicializaciones de la colección) ejecutar.

## <a name="see-also"></a>Vea también
[\\Charla \build 2015](http://channel9.msdn.com/events/Build/2015/3-725)
[completado de código en GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[varios ejemplos en GitHub, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
 [Otros documentos en el sitio de GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
[reglas FxCop implementadas los analizadores de Roslyn en GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
