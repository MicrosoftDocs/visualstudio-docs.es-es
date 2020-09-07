---
title: Analizadores de Roslyn y biblioteca con reconocimiento de código para ImmutableArrays | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b57fb96bf06f5dcafd87e44522575126d7bac55
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509827"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizadores de Roslyn y biblioteca compatible con código para ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [.net Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") le ayuda a crear bibliotecas compatibles con el código. Una biblioteca con reconocimiento de código proporciona funcionalidad que puede usar y herramientas (analizadores de Roslyn) para ayudarle a usar la biblioteca de la mejor manera o para evitar errores. En este tema se muestra cómo crear un analizador Roslyn real para detectar errores comunes al usar el paquete NuGet de [colecciones inmutables NIB](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) . En el ejemplo también se muestra cómo proporcionar una corrección de código para un problema de código encontrado por el analizador. Los usuarios ven correcciones de código en la interfaz de usuario de la bombilla de Visual Studio y pueden aplicar una corrección para el código automáticamente.

## <a name="getting-started"></a>Introducción
Para compilar este ejemplo, necesita lo siguiente:

- Visual Studio 2015 (no una edición Express) o una versión posterior. Puede usar la edición gratuita de [Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs) .

- [SDK de Visual Studio](../extensibility/visual-studio-sdk.md). También puede, al instalar Visual Studio, comprobar Herramientas de extensibilidad de Visual Studio en herramientas comunes para instalar el SDK al mismo tiempo. Si ya ha instalado Visual Studio, también puede instalar este SDK. para ello, vaya al archivo de menú principal **&#124; nuevo &#124;proyecto...**, elija C# en el panel de navegación izquierdo y, a continuación, elija extensibilidad. Cuando se elige la plantilla de proyecto de ruta de navegación "**instalar la herramientas de extensibilidad de Visual Studio**", se le pide que descargue e instale el SDK.

- [SDK de .net Compiler Platform ("Roslyn")](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). También puede instalar este SDK; para ello, vaya al archivo de menú principal **&#124; nuevo &#124; proyecto...**, elija **C#** en el panel de navegación izquierdo y, a continuación, elija **extensibilidad**. Cuando se elige la plantilla de proyecto de ruta de navegación "**descargar el SDK de .net Compiler Platform**", se le pide que descargue e instale el SDK. Este SDK incluye el [Syntax Visualizer Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md). Esta herramienta sumamente útil ayuda a averiguar qué tipos de modelo de código debe buscar en el analizador. La infraestructura del analizador llama al código para los tipos de modelo de código específicos, por lo que el código solo se ejecuta cuando es necesario y solo se puede centrar en el análisis del código relevante.

## <a name="whats-the-problem"></a>¿Cuál es el problema?
Imagine que proporciona una biblioteca con compatibilidad con ImmutableArray (por ejemplo, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> ). Los desarrolladores de C# tienen una gran experiencia con las matrices de .NET. Sin embargo, debido a la naturaleza de las técnicas de ImmutableArrays y optimización utilizadas en la implementación, C# Developer intuitions hace que los usuarios de la biblioteca escriban código roto, como se explica a continuación. Además, los usuarios no ven sus errores hasta el tiempo de ejecución, que no es la experiencia de calidad que se usan en Visual Studio con .NET.

Los usuarios están familiarizados con la escritura de código como el siguiente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Crear matrices vacías para rellenarlas con líneas de código posteriores y usar la sintaxis del inicializador de colección es muy familiar para los desarrolladores de C#. Sin embargo, si se escribe el mismo código para un ImmutableArray se bloquea en tiempo de ejecución:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

El primer error se debe a que la implementación de ImmutableArray usa un struct para encapsular el almacenamiento de datos subyacente. Los Structs deben tener constructores sin parámetros para que `default(T)` las expresiones puedan devolver Structs con todos los miembros cero o null. Cuando el código tiene acceso a `b1.Length` , hay un error de desreferenciación null en tiempo de ejecución porque no hay ninguna matriz de almacenamiento subyacente en el struct ImmutableArray. La manera correcta de crear un ImmutableArray vacío es `ImmutableArray<int>.Empty` .

 El error con inicializadores de colección tiene lugar porque el método ImmutableArray. Add devuelve instancias nuevas cada vez que se llama. Dado que ImmutableArrays nunca cambia, cuando se agrega un nuevo elemento, se obtiene un nuevo objeto ImmutableArray (que puede compartir almacenamiento por motivos de rendimiento con un ImmutableArray existente). Dado `b2` que apunta a la primera ImmutableArray antes `Add()` de llamar a cinco veces, `b2` es un ImmutableArray predeterminado. La longitud de llamada de también se bloquea con un error de desreferenciación null. La manera correcta de inicializar un ImmutableArray sin llamar manualmente a Add es usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Búsqueda de tipos de nodos de sintaxis relevantes para desencadenar el analizador
Para empezar a compilar el analizador, primero debe averiguar qué tipo de SyntaxNode debe buscar.   Inicie el Syntax Visualizer desde la vista de menú **&#124; otros Syntax Visualizer de Windows &#124; Roslyn**.

Coloque el símbolo de intercalación del editor en la línea que declara `b1` . Verá que el Syntax Visualizer muestra que se encuentra en un `LocalDeclarationStatement` nodo del árbol de sintaxis. Este nodo tiene un `VariableDeclaration` , que a su vez tiene un `VariableDeclarator` , que a su vez tiene un `EqualsValueClause` y, por último, hay un `ObjectCreationExpression` . Al hacer clic en el árbol de Syntax Visualizer de nodos, la sintaxis de la ventana del editor se resalta para mostrar el código representado por ese nodo. Los nombres de los subtipos de SyntaxNode coinciden con los nombres que se usan en la gramática de C#.

## <a name="creating-the-analyzer-project"></a>Crear el proyecto de analizador
En el menú principal, elija **archivo &#124; nuevo &#124; proyecto..**.. En el cuadro de diálogo **nuevo proyecto** , en proyectos de **C#** en la barra de navegación de la izquierda, elija extensibilidad y, en el panel derecho, elija la plantilla de proyecto **analizador con corrección de código** . Escriba un nombre y confirme el cuadro de diálogo.

La plantilla abre un archivo DiagnosticAnalyzer.cs. Elija la pestaña búfer del editor. Este archivo tiene una clase de analizador (formada a partir del nombre que asignó al proyecto) que deriva de `DiagnosticAnalyzer` (un tipo de API Roslyn). La nueva clase tiene una `DiagnosticAnalyzerAttribute` declaración el analizador es relevante para el lenguaje C#, de modo que el compilador detecta y carga el analizador.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Puede implementar un analizador mediante Visual Basic que tiene como destino código C# y viceversa. Es más importante en DiagnosticAnalyzerAttribute elegir si el analizador tiene como destino un lenguaje o ambos. Los analizadores más sofisticados que requieren un modelado detallado del lenguaje solo pueden tener como destino un solo idioma. Si, por ejemplo, el analizador solo comprueba los nombres de tipo o los nombres de miembro público, es posible que se puedan usar las ofertas Roslyn de Common Language Model en Visual Basic y C#. Por ejemplo, FxCop advierte que una clase implementa <xref:System.Runtime.Serialization.ISerializable> , pero la clase no tiene el <xref:System.SerializableAttribute> atributo independiente del lenguaje y funciona para el código de Visual Basic y C#.

## <a name="initalizing-the-analyzer"></a>Inicializar el analizador
Desplácese hacia abajo un poco en la `DiagnosticAnalyzer` clase para ver el `Initialize` método. El compilador llama a este método al activar un analizador. El método toma un `AnalysisContext` objeto que permite al analizador obtener información de contexto y registrar devoluciones de llamada para los eventos de los tipos de código que desea analizar.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Abra una nueva línea en este método y escriba "context". para ver una lista de finalización de IntelliSense. Puede ver en la lista de finalización existen muchos `Register…` métodos para controlar diversos tipos de eventos. Por ejemplo, el primero, `RegisterCodeBlockAction` , vuelve a llamar al código para un bloque, que suele ser código entre llaves. El registro de un bloque también llama de nuevo al código para el inicializador de un campo, el valor dado a un atributo o el valor de un parámetro opcional.

Como otro ejemplo, `RegisterCompilationStartAction` , vuelve a llamar al código al principio de una compilación, lo que resulta útil cuando es necesario recopilar el estado en varias ubicaciones. Puede crear una estructura de datos, por ejemplo, para recopilar todos los símbolos usados y, cada vez que se vuelva a llamar al analizador para una sintaxis o un símbolo, puede guardar información sobre cada ubicación en la estructura de datos. Cuando se vuelve a llamar debido a la finalización de la compilación, puede analizar todas las ubicaciones que ha guardado, por ejemplo, para notificar qué símbolos utiliza el código de cada `using` instrucción.

Con el **Syntax Visualizer**, aprendió que quiere que se le llame cuando el compilador procesa un ObjectCreationExpression. Este código se usa para configurar la devolución de llamada:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Regístrese para un nodo de sintaxis y filtre solo por nodos de sintaxis de creación de objetos. Por Convención, los autores del analizador usan una expresión lambda al registrar acciones, lo que ayuda a mantener sin estado los analizadores. Puede usar la característica **generar del uso de** Visual Studio para crear el `AnalyzeObjectCreation` método. Esto genera también el tipo correcto de parámetro de contexto.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Establecer propiedades para los usuarios del analizador
Para que el analizador se muestre correctamente en la interfaz de usuario de Visual Studio, busque y modifique la siguiente línea de código para identificar el analizador:

```csharp
internal const string Category = "Naming";
```

Cambio de `"Naming"` a `"API Guidance"`.

A continuación, busque y abra el archivo resources. resx en el proyecto mediante el **Explorador de soluciones**. Puede incluir una descripción para el analizador, el título, etc. Puede cambiar el valor de todos estos a `“Don’t use ImmutableArray<T> constructor”` por ahora. Puede poner argumentos de formato de cadena en la cadena ( {0} , {1} , etc.) y, más adelante, al llamar a `Diagnostic.Create()` , puede proporcionar una matriz de parámetros de argumentos que se va a pasar.

## <a name="analyzing-an-object-creation-expression"></a>Analizar una expresión de creación de objetos
El `AnalyzeObjectCreation` método toma un tipo diferente de contexto proporcionado por el marco de trabajo del analizador de código. El método Initialize `AnalysisContext` permite registrar devoluciones de llamada de acción para configurar el analizador. El `SyntaxNodeAnalysisContext` , por ejemplo, tiene un `CancellationToken` que se puede pasar. Si un usuario comienza a escribir en el editor, Roslyn cancelará la ejecución de los analizadores para ahorrar trabajo y mejorar el rendimiento. Como otro ejemplo, este contexto tiene una propiedad de nodo que devuelve el nodo de sintaxis de creación de objetos.

Obtenga el nodo, que puede asumir es el tipo para el que ha filtrado la acción del nodo de sintaxis:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Inicio de Visual Studio con el analizador por primera vez
Inicie Visual Studio compilando y ejecutando el analizador (presione **F5**). Dado que el proyecto de inicio del **Explorador de soluciones** es el Proyecto VSIX, al ejecutar el código se compila el código y un VSIX y, a continuación, se inicia Visual Studio con el VSIX instalado. Al iniciar Visual Studio de esta manera, se inicia con un subárbol del registro distinto para que el uso principal de Visual Studio no se vea afectado por las instancias de prueba durante la compilación de analizadores. La primera vez que se inicia de esta manera, Visual Studio realiza varias inicializaciones similares a la primera vez que se inicia Visual Studio después de instalarlo.

 Cree un proyecto de consola y, a continuación, escriba el código de la matriz en el método principal de las aplicaciones de consola:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Las líneas de código `ImmutableArray` que tienen subrayados ondulados deben obtener el paquete NuGet inmutable y agregar una `using` instrucción al código. Presione el botón derecho del puntero en el nodo del proyecto en el **Explorador de soluciones** y elija **administrar paquetes de NuGet..**.. En el administrador de NuGet, escriba "inmutable" en el cuadro de búsqueda y elija el elemento "System. Collections. immutable" (no elija "Microsoft. BCL. immutable") en el panel izquierdo y haga clic en el botón instalar en el panel derecho. Al instalar el paquete, se agrega una referencia a las referencias del proyecto.

Todavía aparecen subrayados ondulados de color rojo en `ImmutableArray` , por lo que debe colocar el símbolo de intercalación en ese identificador y presionar **Ctrl +.** (punto) para que aparezca el menú corregir sugerido y elija Agregar la instrucción adecuada `using` .

**Guarde todos los cambios y cierre** la segunda instancia de Visual Studio para poder continuar.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Finalización del analizador con editar y continuar
En la primera instancia de Visual Studio, establezca un punto de interrupción al principio del `AnalyzeObjectCreation` método presionando **F9** con el símbolo de intercalación en la primera línea.

Vuelva a iniciar el analizador con **F5**y, en la segunda instancia de Visual Studio, vuelva a abrir la aplicación de consola que creó la última vez.

Vuelve a la primera instancia de Visual Studio en el punto de interrupción porque el compilador Roslyn vio una expresión de creación de objeto y se llamaba al analizador.

**Obtiene el nodo de creación del objeto.** Desplazarse por encima de la línea que establece la `objectCreation` variable presionando **F10**y, en la **ventana inmediato** , evalúe la expresión `“objectCreation.ToString()”` . Verá que el nodo de sintaxis al que apunta la variable es el código `"new ImmutableArray<int>()"` , lo que busca.

**Obtiene el \<T> objeto de tipo ImmutableArray.** Debe comprobar si el tipo que se va a crear es ImmutableArray. En primer lugar, obtiene el objeto que representa este tipo. Compruebe los tipos mediante el modelo semántico para asegurarse de que tiene exactamente el tipo correcto y no compare la cadena de ToString (). Escriba la siguiente línea de código al final de la función:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Designe tipos genéricos en metadatos con comillas dobles (') y el número de parámetros genéricos. Esa es la razón por la que no ve "... ImmutableArray \<T> "en el nombre de metadatos.

El modelo semántico tiene muchas cosas útiles que le permiten formular preguntas sobre los símbolos, el flujo de datos, la duración de las variables, etc. Roslyn separa los nodos de sintaxis del modelo semántico por diversos motivos de ingeniería (rendimiento, modelado de código erróneo, etc.). Desea que el modelo de compilación busque información contenida en referencias para una comparación precisa.

Puede arrastrar el puntero de ejecución amarillo en el lado izquierdo de la ventana del editor. Arrástrelo hasta la línea que establece la `objectCreation` variable y recorra la nueva línea de código con **F10**. Si mantiene el puntero del mouse sobre la variable `immutableArrayOfType` , verá que encontramos el tipo exacto en el modelo semántico.

**Obtiene el tipo de la expresión de creación de objetos.** "Type" se usa de varias maneras en este artículo, pero esto significa que si tiene la expresión "New foo", debe obtener un modelo de Foo. Debe obtener el tipo de la expresión de creación de objeto para ver si es el tipo ImmutableArray \<T> . Vuelva a utilizar el modelo semántico para obtener información de símbolos para el símbolo de tipo (ImmutableArray) en la expresión de creación de objeto. Escriba la siguiente línea de código al final de la función:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Dado que el analizador necesita controlar código incompleto o incorrecto en los búferes del editor (por ejemplo, si falta una `using` instrucción), debe comprobar si es `symbolInfo` `null` . Debe obtener un tipo con nombre (INamedTypeSymbol) del objeto de información de símbolos para finalizar el análisis.

**Compare los tipos.** Dado que hay un tipo genérico abierto de T que se está buscando y el tipo en el código es un tipo genérico concreto, se consulta la información de símbolos de la que se construye el tipo (un tipo genérico abierto) y se compara el resultado con `immutableArrayOfTType` . Escriba lo siguiente al final del método:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Notifique el diagnóstico.** La generación de informes del diagnóstico es bastante fácil. La regla que se crea se usa en la plantilla de proyecto, que se define antes del método Initialize. Dado que esta situación en el código es un error, puede cambiar la línea que ha inicializado la regla para reemplazar `DiagnosticSeverity.Warning` (verde ondulado) por `DiagnosticSeverity.Error` (rojo ondulado). El resto de la regla se inicializa a partir de los recursos que editó cerca del principio del tutorial. También debe notificar la ubicación de la línea ondulada, que es la ubicación de la especificación de tipo de expresión de creación de objetos. Escriba este código en el `if` bloque:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La función debe tener el siguiente aspecto (quizás con un formato diferente):

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

Quite el punto de interrupción para que pueda ver que el analizador funciona (y dejar de volver a la primera instancia de Visual Studio). Arrastre el puntero de ejecución al principio del método y presione **F5** para continuar con la ejecución. Cuando vuelva a la segunda instancia de Visual Studio, el compilador comenzará a examinar el código de nuevo y llamará al analizador. Puede ver una línea ondulada en `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Agregar una "corrección de código" para el problema de código
Antes de empezar, cierre la segunda instancia de Visual Studio y detenga la depuración en la primera instancia de Visual Studio (donde está desarrollando el analizador).

**Agregue una nueva clase.** Use el menú contextual (botón de puntero derecho) en el nodo del proyecto en el Explorador de soluciones y elija Agregar un nuevo elemento. Agregue una clase denominada `BuildCodeFixProvider` . Esta clase debe derivar de `CodeFixProvider` y debe usar **Ctrl +.** (punto) para invocar la corrección de código que agrega la `using` instrucción correcta. Esta clase también debe anotarse con `ExportCodeFixProvider` el atributo y deberá agregar una `using` instrucción para resolver la `LanguageNames` enumeración. Debe tener un archivo de clase con el siguiente código:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Código auxiliar de los miembros derivados.** Ahora, coloque el símbolo de intercalación del editor en el identificador `CodeFixProvider` y presione **Ctrl +.** (punto) para realizar el código auxiliar de la implementación para esta clase base abstracta. Esto genera una propiedad y un método.

**Implemente la propiedad.** Rellene el `FixableDiagnosticIds` cuerpo de la propiedad `get` con el código siguiente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn reúne diagnósticos y correcciones mediante la coincidencia de estos identificadores, que son simplemente cadenas. La plantilla de proyecto ha generado un identificador de diagnóstico y puede cambiarla de forma gratuita. El código de la propiedad simplemente devuelve el identificador de la clase de analizador.

**El método RegisterCodeFixAsync toma un contexto.** El contexto es importante porque una corrección de código se puede aplicar a varios diagnósticos o podría haber más de un problema en una línea de código. Si escribe "context". en el cuerpo del método, la lista de finalización de IntelliSense mostrará algunos miembros útiles. Hay un miembro CancellationToken que puede comprobar para ver si algo quiere cancelar la corrección. Hay un miembro del documento que tiene muchos miembros útiles y le permite obtener acceso a los objetos del modelo de proyecto y de la solución. Hay un miembro de intervalo que es el principio y el final de la ubicación de código especificada al informar del diagnóstico.

**Haga que el método sea asincrónico.** Lo primero que debe hacer es corregir la declaración del método generado para que sea un `async` método. La corrección de código para el stub de la implementación de una clase abstracta no incluye la `async` palabra clave aunque el método devuelva un `Task` .

**Obtiene la raíz del árbol de sintaxis.** Para modificar el código, debe generar un nuevo árbol de sintaxis con los cambios que realiza la corrección del código. Necesita del `Document` contexto para llamar a `GetSyntaxRootAsync` . Se trata de un método asincrónico porque hay un trabajo desconocido para obtener el árbol de sintaxis, lo que podría incluir la obtención del archivo desde el disco, su análisis y la creación del modelo de código Roslyn para él. La interfaz de usuario de Visual Studio debe responder durante este tiempo, que usa `async` habilita. Reemplace la línea de código en el método por lo siguiente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Busque el nodo con el problema.** Se pasa el intervalo del contexto, pero es posible que el nodo que encuentre no sea el código que tiene que cambiar. El diagnóstico incluido solo proporcionó el intervalo para el identificador de tipo (donde la línea ondulada pertenecía), pero debe reemplazar la expresión de creación de objeto completa, incluida la `new` keywoard al principio y los paréntesis al final. Agregue el código siguiente al método (y use **Ctrl +.** para agregar una `using` instrucción para `ObjectCreationExpressionSyntax` ):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Registre la corrección del código para la interfaz de usuario de bombillas.** Al registrar la corrección del código, Roslyn se conecta automáticamente a la interfaz de usuario de la bombilla de Visual Studio. Los usuarios finales verán que pueden usar **Ctrl +.** (punto) cuando el analizador subraya en zigzag un uso incorrecto del `ImmutableArray<T>` constructor. Dado que el proveedor de correcciones de código solo se ejecuta cuando hay un problema, puede suponer que tiene la expresión de creación de objeto que estaba buscando. En el parámetro de contexto, puede registrar la nueva corrección de código agregando el código siguiente al final del `RegisterCodeFixAsync` método:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Debe colocar el símbolo de intercalación del editor en el identificador y, `CodeAction` a continuación, usar **Ctrl +.** (punto) para agregar la `using` instrucción adecuada para este tipo.

Después, coloque el símbolo de intercalación del editor en el `ChangeToImmutableArrayEmpty` identificador y use **Ctrl +.** de nuevo para generar este código auxiliar de método.

Este último fragmento de código que ha agregado registra la corrección del código pasando `CodeAction` y el ID. de diagnóstico para el tipo de problema encontrado. En este ejemplo, solo hay un identificador de diagnóstico para el que este código proporciona correcciones, por lo que solo puede pasar el primer elemento de la matriz de identificadores de diagnóstico. Al crear el `CodeAction` , se pasa el texto que la interfaz de usuario de bombilla debe usar como descripción de la corrección del código. También se pasa una función que toma CancellationToken y devuelve un nuevo documento. El nuevo documento tiene un nuevo árbol de sintaxis que incluye el código revisado que llama a `ImmutableArray.Empty` . Este fragmento de código usa una expresión lambda para que pueda cerrarse sobre el nodo objectCreation y el documento del contexto.

**Construya el nuevo árbol de sintaxis.** En el `ChangeToImmutableArrayEmpty` método cuyo código auxiliar haya generado anteriormente, escriba la línea de código: `ImmutableArray<int>.Empty;` . Si vuelve a ver la ventana de herramientas de Syntax Visualizer, puede ver que esta sintaxis es un nodo SimpleMemberAccessExpression. Eso es lo que este método necesita para construir y devolver en un nuevo documento.

El primer cambio en `ChangeToImmutableArrayEmpty` es agregar `async` antes que `Task<Document>` los generadores de código no pueden suponer que el método debe ser asincrónico.

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

Tendrá que colocar el símbolo de intercalación del editor en el `SyntaxGenerator` identificador y usar **Ctrl +.** (punto) para agregar la `using` instrucción adecuada para este tipo.

Este código usa `SyntaxGenerator` , que es un tipo muy útil para construir código nuevo. Después de obtener un generador para el documento que tiene el problema de código, `ChangeToImmutableArrayEmpty` llama a `MemberAccessExpression` , pasando el tipo que tiene el miembro al que queremos acceder y pasando el nombre del miembro como una cadena.

A continuación, el método captura la raíz del documento y, como esto puede implicar un trabajo arbitrario en el caso general, el código espera esta llamada y pasa el token de cancelación. Los modelos de código Roslyn son inmutables, como trabajar con una cadena de .NET; al actualizar la cadena, se obtiene un nuevo objeto de cadena en la devolución. Cuando llame a `ReplaceNode` , recibirá un nuevo nodo raíz. La mayor parte del árbol de sintaxis se comparte (porque es inmutable), pero el `objectCreation` nodo se reemplaza por el `memberAccess` nodo, así como todos los nodos primarios hasta la raíz del árbol de sintaxis.

## <a name="trying-your-code-fix"></a>Prueba de la corrección del código
Ahora puede presionar **F5** para ejecutar el analizador en una segunda instancia de Visual Studio. Abra el proyecto de consola que usó antes. Ahora debería ver la bombilla en la que se muestra la nueva expresión de creación de objetos `ImmutableArray<int>` . Si presiona **Ctrl +.** (punto), verá la corrección del código y verá una vista previa de la diferencia de código generada automáticamente en la interfaz de usuario de bombillas. Roslyn lo crea automáticamente.

Sugerencia Pro: Si inicia la segunda instancia de Visual Studio y no ve la bombilla con la corrección de código, es posible que deba borrar la memoria caché de componentes de Visual Studio. Al borrar la memoria caché se fuerza a Visual Studio a volver a examinar los componentes, por lo que Visual Studio debería seleccionar el componente más reciente. En primer lugar, cierre la segunda instancia de Visual Studio. A continuación, en el explorador de Windows, vaya a su directorio de usuario (c:\Users \\<userid \> ) y busque AppData\Local\Microsoft\VisualStudio\14.0Roslyn \\ . En este directorio, elimine el subdirectorio ComponentModelCache. La versión "14" cambia a la versión con Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Hable de vídeo y finalización del proyecto de código
Puede ver este ejemplo desarrollado y explicado con más detalle en [esta conversación](https://channel9.msdn.com/events/Build/2015/3-725). En el tema se muestra el analizador de trabajo y se le guía en la creación.

[Aquí](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)puede ver todo el código terminado. Cada una de las subcarpetas DoNotUseImmutableArrayCollectionInitializer y DoNotUseImmutableArrayCtor tiene un archivo de C# para buscar problemas y un archivo de C# que implementa las correcciones de código que se muestran en la interfaz de usuario de la bombilla de Visual Studio. Tenga en cuenta que el código terminado tiene un poco más de abstracción para evitar que se recupere el objeto de tipo ImmutableArray una \<T> y otra vez. Utiliza acciones registradas anidadas para guardar el objeto de tipo en un contexto que está disponible cada vez que se ejecutan las subacciones (analizar la creación de objetos y analizar inicializaciones de colección).

## <a name="see-also"></a>Consulte también
[ \\ \Build 2015 hablar](https://channel9.msdn.com/events/Build/2015/3-725)de 
 [código completado en github](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)  
 [varios ejemplos en Github, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
 [otros documentos sobre las](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)reglas de FxCop del sitio OSS de github  
 [implementadas con los analizadores de Roslyn en github](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
