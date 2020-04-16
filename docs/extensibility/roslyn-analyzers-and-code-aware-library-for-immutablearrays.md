---
title: Analizadores Roslyn y Biblioteca compatible con el código para ImmutableArrays Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2076bc9fe3cabbfef8d3f3fb0248724835fa83f5
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444575"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizadores Roslyn y biblioteca compatible con código para ImmutableArrays

La plataforma del compilador de [.NET](https://github.com/dotnet/roslyn) ("Roslyn") le ayuda a crear bibliotecas compatibles con código. Una biblioteca compatible con código proporciona funcionalidad que puede usar y herramientas (analizadores Delyn) para ayudarle a utilizar la biblioteca de la mejor manera o para evitar errores. En este tema se muestra cómo crear un analizador Roslyn del mundo real para detectar errores comunes al usar el paquete NuGet [System.Collections.Immutable.](https://www.nuget.org/packages/System.Collections.Immutable) En el ejemplo también se muestra cómo proporcionar una corrección de código para un problema de código encontrado por el analizador. Los usuarios ven correcciones de código en la interfaz de usuario de bombilla de Visual Studio y pueden aplicar una corrección para el código automáticamente.

## <a name="get-started"></a>Introducción

Necesita lo siguiente para compilar este ejemplo:

* Visual Studio 2015 (no una edición Express) o una versión posterior. Puede usar [visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/) gratuito
* [SDK de Visual Studio](../extensibility/visual-studio-sdk.md). También puede comprobar Visual Studio al instalar Visual Studio, comprobar **Visual Studio Extensibility Tools** en Common **Tools** para instalar el SDK al mismo tiempo. Si ya ha instalado Visual Studio, también puede instalar este SDK yendo al menú principal **Archivo** > **nuevo** > **proyecto**, eligiendo **C-** en el panel de navegación izquierdo y, a continuación, elija **Extensibilidad**. Cuando elige la plantilla de proyecto "Instalar las herramientas de**extensibilidad**de Visual Studio", se le pide que descargue e instale el SDK.
* SDK de [.NET Compiler Platform ("Roslyn")](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). También puede instalar este SDK yendo al menú principal **Archivo** > **nuevo** > **proyecto**, eligiendo **C-** en el panel de navegación izquierdo y, a continuación, eligiendo **Extensibilidad**. Cuando elige **"Descargar el SDK de .NET Compiler Platform"** plantilla de proyecto de ruta de navegación, le pide que descargue e instale el SDK. Este SDK incluye el visualizador de [sintaxis Roslyn.](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer) Esta útil herramienta le ayuda a averiguar qué tipos de modelo de código debe buscar en el analizador. La infraestructura del analizador llama al código para tipos de modelo de código específicos, por lo que el código solo se ejecuta cuando es necesario y solo puede centrarse en analizar el código relevante.

## <a name="whats-the-problem"></a>¿Cuál es el problema?

Imagine que proporciona una biblioteca con compatibilidad <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>con ImmutableArray (por ejemplo, ). Los desarrolladores de CTM tienen mucha experiencia con las matrices de .NET. Sin embargo, debido a la naturaleza de ImmutableArrays y las técnicas de optimización utilizadas en la implementación, las intuiciones de desarrolladores de C- hacen que los usuarios de la biblioteca escriban código roto, como se explica a continuación. Además, los usuarios no ven sus errores hasta el tiempo de ejecución, que no es la experiencia de calidad a la que están acostumbrados en Visual Studio con .NET.

Los usuarios están familiarizados con escribir código como el siguiente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

La creación de matrices vacías para rellenar con líneas de código posteriores y el uso de la sintaxis del inicializador de colección son familiares para los desarrolladores de C. Sin embargo, al escribir el mismo código para un ImmutableArray se bloquea en tiempo de ejecución:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

El primer error se debe a que la implementación de ImmutableArray usa una estructura para ajustar el almacenamiento de datos subyacente. Las estructuras deben tener constructores `default(T)` sin parámetros para que las expresiones puedan devolver structs con todos los miembros cero o nulo. Cuando el código `b1.Length`tiene acceso, hay un error de desreferencia nula en tiempo de ejecución porque no hay ninguna matriz de almacenamiento subyacente en la estructura ImmutableArray. La forma correcta de crear un `ImmutableArray<int>.Empty`ImmutableArray vacío es .

El error con inicializadores de `ImmutableArray.Add` colección se produce porque el método devuelve nuevas instancias cada vez que se llama. Dado que ImmutableArrays nunca cambia, cuando se agrega un nuevo elemento, se obtiene un nuevo objeto ImmutableArray (que puede compartir el almacenamiento por motivos de rendimiento con un ImmutableArray existente anteriormente). Dado `b2` que apunta a la primera `Add()` ImmutableArray antes de llamar cinco veces, `b2` es un valor predeterminado ImmutableArray. Llamar a Length en él también se bloquea con un error de desreferencia nulo. La forma correcta de inicializar un ImmutableArray sin llamar manualmente a Add es usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Buscar tipos de nodos de sintaxis relevantes para activar el analizador

 Para comenzar a compilar el analizador, primero averiguar qué tipo de SyntaxNode necesita buscar. Inicie el visualizador de **sintaxis** desde el menú **Ver** > **otro** > visualizador de**sintaxis Roslyn**de Windows .

Coloque el intercalador del editor en `b1`la línea que declara . Verá que el visualizador de sintaxis `LocalDeclarationStatement` muestra que se encuentra en un nodo del árbol de sintaxis. Este nodo tiene `VariableDeclaration`un , que `VariableDeclarator`a su vez `EqualsValueClause`tiene un , `ObjectCreationExpression`que a su vez tiene un , y finalmente hay un . Al hacer clic en el árbol de nodos del visualizador de sintaxis, la sintaxis de la ventana del editor se resalta para mostrarle el código representado por ese nodo. Los nombres de los subtipos SyntaxNode coinciden con los nombres utilizados en la gramática de C.

## <a name="create-the-analyzer-project"></a>Crear el proyecto de analizador

En el menú principal, elija **Archivo** > **nuevo** > **proyecto**. En el cuadro de diálogo **Nuevo proyecto,** en Proyectos de **C,** en la barra de navegación izquierda, elija **Extensibilidad**y, en el panel derecho, elija la plantilla de proyecto **Analizador con corrección** de código. Introduzca un nombre y confirme el cuadro de diálogo.

La plantilla abre un archivo *DiagnosticAnalyzer.cs.* Elija esa pestaña del búfer del editor. Este archivo tiene una clase de analizador (formada a partir `DiagnosticAnalyzer` del nombre que dio al proyecto) que deriva de (un tipo de API Roslyn). La nueva clase `DiagnosticAnalyzerAttribute` tiene un declaring el analizador es relevante para el lenguaje de C- para que el compilador detecte y cargue el analizador.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Puede implementar un analizador mediante Visual Basic que tenga como destino el código de C- y viceversa. Es más importante en DiagnosticAnalyzerAttribute elegir si el analizador tiene como destino un idioma o ambos. Los analizadores más sofisticados que requieren un modelado detallado del lenguaje solo pueden dirigirse a un único idioma. Si el analizador, por ejemplo, solo comprueba los nombres de tipo o los nombres de miembros públicos, es posible usar el modelo de lenguaje común que Roslyn ofrece en Visual Basic y C. Por ejemplo, FxCop advierte que <xref:System.Runtime.Serialization.ISerializable>se implementa una clase <xref:System.SerializableAttribute> , pero la clase no tiene el atributo es independiente del lenguaje y funciona para Visual Basic y el código de C.

## <a name="initialize-the-analyzer"></a>Inicializar el analizador

 Desplácese hacia abajo `DiagnosticAnalyzer` un poco `Initialize` en la clase para ver el método. El compilador llama a este método al activar un analizador. El método `AnalysisContext` toma un objeto que permite al analizador obtener información de contexto y registrar devoluciones de llamada para eventos para los tipos de código que desea analizar.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Abra una nueva línea en este método y escriba "context." para ver una lista de finalización de IntelliSense. Puede ver en la lista `Register...` de finalización hay muchos métodos para controlar varios tipos de eventos. Por ejemplo, el `RegisterCodeBlockAction`primero, , vuelve a llamar al código de un bloque, que suele ser código entre llaves. Registrarse para un bloque también vuelve a llamar al código para el inicializador de un campo, el valor dado a un atributo o el valor de un parámetro opcional.

Como otro `RegisterCompilationStartAction`ejemplo, , vuelve a llamar al código al inicio de una compilación, lo que resulta útil cuando necesita recopilar el estado en muchas ubicaciones. Puede crear una estructura de datos, por ejemplo, para recopilar todos los símbolos utilizados y cada vez que se llame al analizador para alguna sintaxis o símbolo, puede guardar información sobre cada ubicación en la estructura de datos. Cuando se le llama de nuevo debido al final de la compilación, puede analizar todas las `using` ubicaciones que guardó, por ejemplo, para informar de qué símbolos utiliza el código de cada instrucción.

Mediante el visualizador de **sintaxis**, aprendió que desea que se le llame cuando el compilador procesa un ObjectCreationExpression. Utilice este código para configurar la devolución de llamada:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Se registra para un nodo de sintaxis y se filtra solo para los nodos de sintaxis de creación de objetos. Por convención, los autores del analizador usan una lambda al registrar acciones, lo que ayuda a mantener los analizadores sin estado. Puede usar la característica de Visual Studio `AnalyzeObjectCreation` Generar a partir del **uso** para crear el método. Esto también genera el tipo correcto de parámetro de contexto para usted.

## <a name="set-properties-for-users-of-your-analyzer"></a>Establecer propiedades para los usuarios del analizador

Para que el analizador aparezca en la interfaz de usuario de Visual Studio de forma adecuada, busque y modifique la siguiente línea de código para identificar el analizador:

```csharp
internal const string Category = "Naming";
```

Cambio de `"Naming"` a `"API Guidance"`.

A continuación, busque y abra el archivo *Resources.resx* en el proyecto mediante el Explorador de **soluciones**. Puede poner una descripción para su analizador, título, etc. Puede cambiar el valor de `"Don't use ImmutableArray<T> constructor"` todos estos por ahora. Puede colocar argumentos de formato{0}de {1}cadena en la cadena `Diagnostic.Create()`( , , `params` etc.) y, más adelante, cuando llame a , puede proporcionar una matriz de argumentos que se pasarán.

## <a name="analyze-an-object-creation-expression"></a>Analizar una expresión de creación de objetos

El `AnalyzeObjectCreation` método toma un tipo diferente de contexto proporcionado por el marco del analizador de código. El `Initialize` método `AnalysisContext` le permite registrar devoluciones de llamada de acción para configurar el analizador. El `SyntaxNodeAnalysisContext`, por ejemplo, tiene un `CancellationToken` que se puede pasar. Si un usuario comienza a escribir en el editor, Roslyn cancelará los analizadores en ejecución para guardar el trabajo y mejorar el rendimiento. Como otro ejemplo, este contexto tiene una propiedad Node que devuelve el nodo de sintaxis de creación de objetos.

Obtenga el nodo, que puede suponer que es el tipo para el que filtró la acción del nodo de sintaxis:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Inicie Visual Studio con el analizador la primera vez

Inicie Visual Studio creando y ejecutando el analizador (presione **F5**). Dado que el proyecto de inicio en el **Explorador** de soluciones es el proyecto VSIX, al ejecutar el código se compila el código y un VSIX y, a continuación, se inicia Visual Studio con ese VSIX instalado. Al iniciar Visual Studio de esta manera, se inicia con un subárbol del Registro distinto para que el uso principal de Visual Studio no se vea afectado por las instancias de prueba al compilar analizadores. La primera vez que se inicia de esta manera, Visual Studio realiza varias inicializaciones similares a la primera vez que inició Visual Studio después de instalarlo.

Cree un proyecto de consola y, a continuación, escriba el código de matriz en las aplicaciones de consola Método principal:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Las líneas de `ImmutableArray` código con tienen ondulaciones porque necesita obtener el `using` paquete NuGet inmutable y agregar una instrucción al código. Presione el botón del puntero derecho en el nodo del proyecto en el **Explorador** de soluciones y elija **Administrar paquetes NuGet**. En el Administrador de NuGet, escriba "Immutable" en el cuadro de búsqueda y elija el elemento **System.Collections.Immutable** (no elija **Microsoft.Bcl.Immutable**) en el panel izquierdo y presione el botón **Instalar** en el panel derecho. La instalación del paquete agrega una referencia a las referencias del proyecto.

Todavía verá ondulaciones `ImmutableArray`rojas debajo, así que coloque el intercalador en ese identificador y presione **Ctrl**+**.** (período) para abrir el menú de arreglos `using` sugerido y elegir agregar la instrucción apropiada.

**Guardar todo y cerrar** la segunda instancia de Visual Studio por ahora para poner en un estado limpio para continuar.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Finalice el analizador utilizando editar y continuar

En la primera instancia de Visual Studio, establezca `AnalyzeObjectCreation` un punto de interrupción al principio del método presionando **F9** con el intercalador en la primera línea.

Vuelva a iniciar el analizador con **F5**y, en la segunda instancia de Visual Studio, vuelva a abrir la aplicación de consola que creó la última vez.

Vuelve a la primera instancia de Visual Studio en el punto de interrupción porque el compilador de Roslyn vio una expresión de creación de objetos y llamó al analizador.

**Obtener el nodo de creación de objetos.** Pase por encima `objectCreation` de la línea que establece la variable presionando **F10**y, en la **ventana Inmediato,** evalúe la expresión. `"objectCreation.ToString()"` Verá que el nodo de sintaxis al `"new ImmutableArray<int>()"`que apunta la variable es el código, justo lo que está buscando.

**Obtener ImmutableArray\><T Type objeto.** Debe comprobar si el tipo que se está creando es ImmutableArray. En primer lugar, obtendrá el objeto que representa este tipo. Compruebe los tipos mediante el modelo semántico para asegurarse de que `ToString()`tiene exactamente el tipo correcto y no se compara la cadena de . Introduzca la siguiente línea de código al final de la función:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Los tipos genéricos se designan en metadatos con backticks (') y el número de parámetros genéricos. Es por eso que no ves "... ImmutableArray\<T>" en el nombre de los metadatos.

El modelo semántico tiene muchas cosas útiles que le permiten hacer preguntas sobre símbolos, flujo de datos, duración variable, etc. Roslyn separa los nodos de sintaxis del modelo semántico por varias razones de ingeniería (rendimiento, modelado de código erróneo, etc.). Desea que el modelo de compilación busque la información contenida en las referencias para una comparación precisa.

Puede arrastrar el puntero de ejecución amarillo en el lado izquierdo de la ventana del editor. Arrástrelo hasta la `objectCreation` línea que establece la variable y pase por encima de la nueva línea de código con **F10**. Si coloca el puntero del `immutableArrayOfType`ratón sobre la variable , verá que hemos encontrado el tipo exacto en el modelo semántico.

**Obtenga el tipo de la expresión de creación de objetos.** "Tipo" se utiliza de varias maneras en este artículo, pero esto significa que si tiene sesión "nueva Foo", necesita obtener un modelo de Foo. Debe obtener el tipo de la expresión de creación de objetos para ver si es el tipo de> ImmutableArray\<T. Utilice el modelo semántico de nuevo para obtener información de símbolo para el símbolo de tipo (ImmutableArray) en la expresión de creación de objetos. Introduzca la siguiente línea de código al final de la función:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Dado que el analizador debe controlar código incompleto o incorrecto en `using` los búferes del `symbolInfo` `null`editor (por ejemplo, falta una instrucción), debe comprobar si es . Debe obtener un tipo con nombre (INamedTypeSymbol) del objeto de información de símbolo para finalizar el análisis.

**Compare los tipos.** Dado que hay un tipo genérico abierto de T que estamos buscando y el tipo en el código es un tipo genérico concreto, consulta la `immutableArrayOfTType`información del símbolo para lo que se construye el tipo (un tipo genérico abierto) y se compara ese resultado con . Introduzca lo siguiente al final del método:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Informe del diagnóstico.** Informar del diagnóstico es bastante fácil. Utilice la regla creada para usted en la plantilla de proyecto, que se define antes de la Initialize método. Dado que esta situación en el código es un error, `DiagnosticSeverity.Warning` puede cambiar la línea `DiagnosticSeverity.Error` que inicializó Rule para reemplazar (green squiggle) con (red squiggle). El resto de la regla se inicializa a partir de los recursos que editó cerca del principio del tutorial. También debe informar de la ubicación del squiggle, que es la ubicación de la especificación de tipo de la expresión de creación de objetos. Introduzca este código `if` en el bloque:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La función debería tener este aspecto (quizás con un formato diferente):

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

Quite el punto de interrupción para que pueda ver el analizador funcionando (y dejar de volver a la primera instancia de Visual Studio). Arrastre el puntero de ejecución al principio del método y presione **F5** para continuar la ejecución. Cuando vuelva a la segunda instancia de Visual Studio, el compilador comenzará a examinar el código de nuevo y llamará al analizador. Se puede ver un ondulación debajo `ImmutableType<int>`de .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Adición de una "corrección de código" para el problema de código

Antes de comenzar, cierre la segunda instancia de Visual Studio y detenga la depuración en la primera instancia de Visual Studio (donde está desarrollando el analizador).

**Agregue una nueva clase.** Use el menú contextual (botón de puntero derecho) en el nodo del proyecto en el **Explorador** de soluciones y elija agregar un nuevo elemento. Agregue una `BuildCodeFixProvider`clase denominada . Esta clase debe `CodeFixProvider`derivar de , y deberá usar **Ctrl**+**.** (período) para invocar la corrección `using` de código que agrega la instrucción correcta. Esta clase también debe anotarse con `ExportCodeFixProvider` attribute y `using` deberá agregar `LanguageNames` una instrucción para resolver la enumeración. Debe tener un archivo de clase con el siguiente código:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Stub out miembros derivados.** Ahora, coloque el intercalador del `CodeFixProvider` editor en el identificador y presione **Ctrl**+**.** (período) para eliminar la implementación de esta clase base abstracta. Esto genera una propiedad y un método para usted.

**Implemente la propiedad.** Rellene el `FixableDiagnosticIds` cuerpo `get` de la propiedad con el siguiente código:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn reúne diagnósticos y correcciones haciendo coincidir estos identificadores, que son solo cadenas. La plantilla de proyecto generó un identificador de diagnóstico para usted y puede cambiarlo. El código de la propiedad solo devuelve el identificador de la clase de analizador.

**El registerCodeFixAsync método toma un contexto.** El contexto es importante porque una corrección de código se puede aplicar a varios diagnósticos o puede haber más de un problema en una línea de código. Si escribe "contexto." en el cuerpo del método, la lista de finalización de IntelliSense le mostrará algunos miembros útiles. Hay un miembro CancellationToken que puede comprobar para ver si algo desea cancelar la corrección. Hay un miembro Document que tiene muchos miembros útiles y le permite llegar a los objetos de modelo de proyecto y solución. Hay un miembro Span que es el inicio y el final de la ubicación del código especificado cuando notificó el diagnóstico.

**Haga que el método sea asincrónico.** Lo primero que debe hacer es corregir la declaración de método generada para que sea un `async` método. La corrección de código para stubbing out la `async` implementación de una `Task`clase abstracta no incluye la palabra clave aunque el método devuelve un archivo .

**Obtenga la raíz del árbol de sintaxis.** Para modificar el código, debe generar un nuevo árbol de sintaxis con los cambios que realiza la corrección de código. Necesita el `Document` desde el `GetSyntaxRootAsync`contexto para llamar a . Este es un método asincrónico porque hay trabajo desconocido para obtener el árbol de sintaxis, posiblemente incluyendo obtener el archivo del disco, analizarlo y compilar el modelo de código Roslyn para él. La interfaz de usuario de Visual `async` Studio debe responder durante este tiempo, lo que permite. Reemplace la línea de código del método por la siguiente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Busque el nodo con el problema.** Se pasa en el intervalo del contexto, pero el nodo que encuentra puede no ser el código que tiene que cambiar. El diagnóstico notificado solo proporcionaba el intervalo para el identificador de tipo (donde pertenecía el squiggle), pero debe reemplazar toda la expresión de creación de objetos, incluida la `new` palabra clave al principio y los paréntesis al final. Agregue el código siguiente al método (y use **Ctrl**+**.** para añadir `using` una `ObjectCreationExpressionSyntax`declaración para ):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registre la corrección de código para la interfaz de usuario de la bombilla.** Al registrar la corrección de código, Roslyn se conecta automáticamente a la interfaz de usuario de bombilla de Visual Studio. Los usuarios finales verán que pueden usar **Ctrl**+**.** (período) cuando el analizador se `ImmutableArray<T>` ondea un mal uso del constructor. Dado que el proveedor de corrección de código solo se ejecuta cuando hay un problema, puede suponer que tiene la expresión de creación de objetos que estaba buscando. Desde el parámetro context, puede registrar la nueva corrección de `RegisterCodeFixAsync` código agregando el siguiente código al final del método:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Debe colocar el intercalador del editor `CodeAction`en el identificador y, a continuación, usar **Ctrl**+**.** (período) para agregar `using` la declaración adecuada para este tipo.

A `ChangeToImmutableArrayEmpty` continuación, coloque el intercalador del editor en el identificador y utilice **Ctrl**+**.** de nuevo para generar este código auxiliar de método para usted.

Este último fragmento de código que agregó `CodeAction` registra la corrección de código pasando un identificador de diagnóstico y el identificador de diagnóstico para el tipo de problema encontrado. En este ejemplo, solo hay un identificador de diagnóstico para el que este código proporciona correcciones, por lo que puede pasar el primer elemento de la matriz de identificadores de diagnóstico. Al crear `CodeAction`el , se pasa el texto que la interfaz de usuario de bombilla debe usar como descripción de la corrección de código. También se pasa una función que toma un CancellationToken y devuelve un nuevo documento. El nuevo documento tiene un nuevo árbol de `ImmutableArray.Empty`sintaxis que incluye el código parcheado que llama a . Este fragmento de código utiliza una expresión lambda para que pueda cerrarse sobre el nodo objectCreation y el documento del contexto.

**Construya el nuevo árbol de sintaxis.** En `ChangeToImmutableArrayEmpty` el método cuyo código auxiliar generó anteriormente, `ImmutableArray<int>.Empty;`escriba la línea de código: . Si vuelve a ver la ventana de herramientas Visualizador de **sintaxis,** puede ver que esta sintaxis es un nodo SimpleMemberAccessExpression. Eso es lo que este método necesita para construir y devolver en un nuevo documento.

El primer `ChangeToImmutableArrayEmpty` cambio es `async` `Task<Document>` agregar antes porque los generadores de código no pueden asumir que el método debe ser asincrónico.

Rellene el cuerpo con el código siguiente para que el método tenga un aspecto similar al siguiente:

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

Tendrá que poner el intercalador del `SyntaxGenerator` editor en el identificador y usar **Ctrl**+**.** (período) para agregar `using` la declaración adecuada para este tipo.

Este código `SyntaxGenerator`usa , que es un tipo útil para construir código nuevo. Después de obtener un generador para `ChangeToImmutableArrayEmpty` el `MemberAccessExpression`documento que tiene el problema de código, llama , pasando el tipo que tiene el miembro al que queremos tener acceso y pasando el nombre del miembro como una cadena.

A continuación, el método recupera la raíz del documento y, dado que esto puede implicar un trabajo arbitrario en el caso general, el código espera esta llamada y pasa el token de cancelación. Los modelos de código Roslyn son inmutables, como trabajar con una cadena .NET; cuando se actualiza la cadena, se obtiene un nuevo objeto de cadena a cambio. Cuando se `ReplaceNode`llama , se obtiene un nuevo nodo raíz. La mayor parte del árbol de sintaxis se `objectCreation` comparte (porque es `memberAccess` inmutable), pero el nodo se reemplaza por el nodo, así como todos los nodos primarios hasta la raíz del árbol de sintaxis.

## <a name="try-your-code-fix"></a>Pruebe la corrección de código

Ahora puede presionar **F5** para ejecutar el analizador en una segunda instancia de Visual Studio. Abra el proyecto de consola que utilizó anteriormente. Ahora debería ver que la bombilla aparece donde `ImmutableArray<int>`está la nueva expresión de creación de objetos. Si pulsa **Ctrl**+**.** (período), verá la corrección de código y verá una vista previa de la diferencia de código generada automáticamente en la interfaz de usuario de la bombilla. Roslyn crea esto para ti.

**Consejo Profesional:** Si inicia la segunda instancia de Visual Studio y no ve la bombilla con la corrección de código, es posible que deba borrar la caché de componentes de Visual Studio. Borrar la memoria caché obliga a Visual Studio a volver a examinar los componentes, por lo que Visual Studio debe recoger el componente más reciente. En primer lugar, cierre la segunda instancia de Visual Studio. A continuación, en el Explorador de **Windows**, desplácese hasta *%LOCALAPPDATA%-Microsoft-VisualStudio-16.0Roslyn\\*. (El "16.0" cambia de versión a versión con Visual Studio.) Elimine el subdirectorio *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Hablar de vídeo y terminar el proyecto de código

Puede ver este ejemplo desarrollado y discutido más adelante en [esta charla](https://channel9.msdn.com/events/Build/2015/3-725). La charla demuestra el analizador de trabajo y le guía a través de la construcción de la misma.

Puede ver todo el código terminado [aquí](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Las subcarpetas *DoNotUseImmutableArrayCollectionInitializer* y *DoNotUseImmutableArrayCtor* tienen cada una un archivo de C- para buscar problemas y un archivo de C- que implementa las correcciones de código que aparecen en la interfaz de usuario de bombilla de Visual Studio. Tenga en cuenta que el código terminado tiene un poco más\<de abstracción para evitar la obtención de la immutableArray T> objeto de tipo una y otra vez. Utiliza acciones registradas anidadas para guardar el objeto de tipo en un contexto que está disponible siempre que se ejecuten las subacciones (analizar la creación de objetos y analizar las inicializaciones de la colección).

## <a name="see-also"></a>Consulte también

* [\\Charla de la construcción de 2015](https://channel9.msdn.com/events/Build/2015/3-725)
* [Código completado en GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Varios ejemplos en GitHub, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Otros documentos en el sitio de GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Reglas de FxCop implementadas con analizadores Roslyn en GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
