---
title: "Analizadores de Roslyn y tenga en cuenta el c&#243;digo de biblioteca para ImmutableArrays | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Analizadores de Roslyn y tenga en cuenta el c&#243;digo de biblioteca para ImmutableArrays
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El [plataforma del compilador .NET](https://github.com/dotnet/roslyn) \(«Roslyn»\) le ayuda a crear bibliotecas de código.  Una biblioteca de código proporciona funcionalidad que puede usar y herramientas \(analizadores de Roslyn\) para utilizar la biblioteca de la mejor manera o para evitar errores.  Este tema muestra cómo crear un analizador de Roslyn del mundo real para detectar errores comunes al utilizar el [Colecciones inmutables](../Topic/NIB:%20Immutable%20Collections.md) paquete NuGet.  El ejemplo también muestra cómo proporcionar una revisión de código para un problema de código que se encuentra el analizador.  Los usuarios ver las correcciones de código en la interfaz de usuario de Visual Studio una bombilla y pueden aplicar una corrección para el código automáticamente.  
  
## En este tema  
 Este tema contiene las siguientes secciones:  
  
-   Introducción  
  
-   ¿Cuál es el problema?  
  
-   Buscar los tipos de modelo de código relevante para desencadenar el analizador  
  
-   Crear el proyecto de Analyzer  
  
-   Inicializar el analizador  
  
-   Establecer propiedades para los usuarios de su analizador  
  
-   Analizar una expresión de creación de objeto  
  
-   Inicio de Visual Studio con el analizador de la primera vez  
  
-   Finalizando el analizador utilizando Editar y continuar  
  
-   Agregar una "revisión de código" para el problema de código  
  
-   Probar la corrección de código  
  
-   Proyecto de código de vídeo y termine de hablar  
  
## Introducción  
 Necesita lo siguiente para compilar este ejemplo:  
  
-   Visual Studio 2015 \(no una versión Express Edition\) o una versión posterior.  Puede usar el libre [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  También puede, al instalar Visual Studio, comprobar herramientas de extensibilidad de Visual Studio en herramientas comunes para instalar el SDK al mismo tiempo.  Si ya ha instalado Visual Studio, también puede instalar este SDK, vaya al menú principal **archivo &#124; Nuevo &#124; Proyecto**, elija C\# en el panel de navegación izquierdo y, a continuación, elija extensibilidad.  Cuando se elige el "**instalar las herramientas de extensibilidad de Visual Studio**" plantilla de proyecto de la ruta de navegación, que le pedirá que descargue e instale el SDK.  
  
-   [.NET compiler Platform \(«Roslyn»\) SDK](http://aka.ms/roslynsdktemplates).  También puede instalar este SDK, vaya al menú principal **archivo &#124; Nuevo &#124; Proyecto**, elija **C\#** en el panel de navegación izquierdo y, a continuación, seleccionando **extensibilidad**.  Cuando se elige "**descargar el SDK de plataforma del compilador .NET**" plantilla de proyecto de la ruta de navegación, que le pedirá que descargue e instale el SDK.  Este SDK incluye la [Visualizador de sintaxis Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Esta herramienta extremadamente útil le ayuda a descubrir qué tipos de modelo de código debe buscar en el analizador.  Las llamadas de la infraestructura de analizador en el código para tipos de modelo de código específico, por lo que el código sólo se ejecuta cuando sea necesario y puede centrarse sólo en el análisis de código relevante.  
  
## ¿Cuál es el problema?  
 Imagine que proporciona una biblioteca de ImmutableArray \(por ejemplo, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) admiten.  Los desarrolladores de C\# tienen mucha experiencia con matrices. NET.  Sin embargo, debido a la naturaleza de las técnicas de optimización y ImmutableArrays que se usa en la implementación, intuitions para desarrolladores de C\# que los usuarios de la biblioteca escribir código roto, tal como se explica a continuación.  Además, los usuarios no ven sus errores de tiempo de ejecución, lo que no se utilizan en Visual Studio con .NET para la experiencia de calidad.  
  
 Los usuarios están familiarizados con la escritura de código como el siguiente:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Creación de matrices vacías a rellenar con las siguientes líneas de código y utilizando la sintaxis del inicializador de colección son muy familiares para los desarrolladores de C\#.  Sin embargo, escribir el mismo código para un ImmutableArray sufre un error en tiempo de ejecución:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 El primer error es debido a que la implementación ImmutableArray utiliza una estructura para ajustar el almacenamiento de datos subyacente.  Las estructuras deben tener constructores sin parámetros para que `default(T)` las expresiones pueden devolver structs con todas cero o nulos miembros.  Cuando el código tiene acceso a `b1.Length`, hay un valor null de tiempo de ejecución de desreferenciación error porque no hay ninguna matriz de almacenamiento subyacente de la estructura ImmutableArray.  La manera correcta para crear un ImmutableArray vacía es `ImmutableArray<int>.Empty`.  
  
 El error con inicializadores de colección se produce porque el método ImmutableArray.Add devuelve instancias nuevo cada vez que lo llama.  Porque ImmutableArrays nunca cambia, al agregar un nuevo elemento, obtendrá un nuevo objeto ImmutableArray \(que puede compartir el almacenamiento por motivos de rendimiento con un ImmutableArray ya existente\).  Porque `b2` apunta a la primera ImmutableArray antes de llamar a `Add()` cinco veces, `b2` es el valor predeterminado es ImmutableArray.  Error de desreferenciación de llamar a longitud en él también se bloquea con un valor null.  La manera correcta de inicializar un ImmutableArray sin llamar manualmente a agregar es usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.  
  
## Buscar los tipos de nodo de sintaxis relevantes para desencadenar el analizador  
 Para comenzar a crear el analizador, en primer lugar averiguar qué tipo de SyntaxNode debe buscar.    Iniciar el visualizador de sintaxis en el menú **vista &#124; Otras ventanas &#124; Visualizador de sintaxis Roslyn**.  
  
 Colocar el símbolo de intercalación del editor en la línea que declara `b1`.  Verá el visualizador de sintaxis muestra que se encuentra en un `LocalDeclarationStatement` nodo del árbol de sintaxis.  Este nodo tiene un `VariableDeclaration`, que a su vez tiene un `VariableDeclarator`, que a su vez tiene un `EqualsValueClause`, y por último, hay un `ObjectCreationExpression`.  Al hacer clic en el árbol del visualizador de sintaxis de nodos, la sintaxis en la ventana del editor resalta para mostrar el código representado por ese nodo.  Los nombres de los tipos de sub SyntaxNode coinciden con los nombres utilizados en la gramática de C\#.  
  
## Crear el proyecto de Analyzer  
 En el menú principal, elija **archivo &#124; Nuevo &#124; Proyecto**.  En el **nuevo proyecto** cuadro de diálogo, en **C\#** proyectos en la barra de navegación izquierdo, seleccione extensibilidad y en el panel derecho, elija la **Analizador con corrección de código** plantilla de proyecto.  Escriba un nombre y confirme el cuadro de diálogo.  
  
 La plantilla abre un archivo DiagnosticAnalyzer.cs.  Elija a ese editor ficha de búfer.  Este archivo tiene una clase de analizador \(el formato del nombre que dio al proyecto\) que se deriva de `DiagnosticAnalyzer` \(un tipo de API de Roslyn\).  La nueva clase tiene un `DiagnosticAnalyzerAttribute` declarar el analizador es relevante para el lenguaje C\# para que el compilador detecta y carga el analizador.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Puede implementar un analizador utilizando Visual Basic que tenga como destino el código C\#, y viceversa.  Es más importante en el DiagnosticAnalyzerAttribute para elegir si el analizador dirige a un idioma o ambos.  Analizadores más sofisticados que requieren modelado detallado del lenguaje sólo pueden tener como destino un único idioma.  Si el analizador, por ejemplo, sólo comprueba los nombres de tipo o miembro público, es posible usar el modelo de lenguaje común que ofrece Roslyn en Visual Basic y C\#.  Por ejemplo, FxCop advierte que una clase implementa <xref:System.Runtime.Serialization.ISerializable>, pero la clase no tiene la <xref:System.SerializableAttribute> atributo es independiente del lenguaje y funciona para código de Visual Basic y C\#.  
  
## Inicializar el analizador  
 Desplácese hacia abajo un poco en la `DiagnosticAnalyzer` clase para ver el `Initialize` método.  El compilador llama a este método cuando se activa un analizador.  El método toma un `AnalysisContext` objeto que permite el analizador para obtener información de contexto y registrar devoluciones de llamada de eventos para los tipos de código que desea analizar.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Abrir una nueva línea en este método y el tipo "contexto". Para ver una lista de finalización de Intellisense.  Puede ver la lista de finalización hay muchos `Register…` métodos para controlar los distintos tipos de eventos.  Por ejemplo, la primera de ellas, `RegisterCodeBlockAction`, las llamadas al código de un bloque, que suele ser código entre llaves.  Registrar para un bloque también vuelve a llamar al código para el inicializador de un campo, el valor del atributo o el valor de un parámetro opcional.  
  
 Como otro ejemplo, `RegisterCompilationStartAction`, las llamadas al código al comienzo de una compilación, lo que resulta útil cuando necesita recopilar estado en varias ubicaciones.  Puede crear una estructura de datos, por ejemplo, para recopilar todos los símbolos que se utilizan, y cada vez que el analizador vuelve a llamar para algunas sintaxis o símbolo, puede guardar información acerca de cada ubicación en la estructura de datos.  Cuando se llama volver debido a la finalización de la compilación, puede analizar todas las ubicaciones de guardado, por ejemplo, para informar de los símbolos que se utiliza el código de cada `using` instrucción.  
  
 Mediante el **Visualizador de sintaxis**, ha aprendido que desea que se llama cuando el compilador procesa un ObjectCreationExpression.  Use este código para configurar la devolución de llamada:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Registrar para un nodo de la sintaxis y el filtro para sólo nodos de sintaxis de objeto creación.  Por convención, los autores de analizador utilizan una expresión lambda cuando registra las acciones, lo que ayuda a mantener los analizadores sin estado.  Puede usar la característica de Visual Studio **Generate From Usage** para crear el `AnalyzeObjectCreation` método.  Esto genera el tipo de parámetro de contexto correcto demasiado.  
  
## Establecer propiedades para los usuarios de su analizador  
 Para que el analizador se muestre en la interfaz de usuario de Visual Studio correctamente, busque y modifique la siguiente línea de código para identificar el analizador:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Cambio de `"Naming"` a `"API Guidance"`.  
  
 A continuación busque y abra el archivo Resources.resx en el proyecto con el **el Explorador de soluciones**.  Puede colocar en una descripción para el analizador, título, etc..  Puede cambiar el valor de todos a `“Don’t use ImmutableArray<T> constructor”` por ahora.  Puede colocar los argumentos en la cadena de formato de cadena \({0}, \\{1\\}, etc.\) y versiones posteriores cuando se llama a `Diagnostic.Create()`, puede proporcionar una matriz de parámetros de argumentos que se pasan.  
  
## Analizar una expresión de creación de objeto  
 El `AnalyzeObjectCreation` método toma un tipo diferente de contexto proporcionado por el marco de trabajo del analizador de código.  El método Initialize `AnalysisContext` le permite registrar devoluciones de llamada de acción para configurar el analizador.  El `SyntaxNodeAnalysisContext`, por ejemplo, tiene un `CancellationToken` que puede pasar.  Si un usuario empieza a escribir en el editor, Roslyn cancelar la ejecución analizadores para guardar el trabajo y mejorar el rendimiento.  Como otro ejemplo, este contexto tiene una propiedad de nodo que devuelve el nodo de sintaxis de creación de objeto.  
  
 Obtiene el nodo, que se puede suponer que es el tipo para el que se filtra la acción de nodo de sintaxis:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### Inicio de Visual Studio con el analizador de la primera vez  
 Inicie Visual Studio al compilar y ejecutar el analizador \(presione **F5**\).  Porque el inicio del proyecto en el **el Explorador de soluciones** el proyecto VSIX, que se ejecutan las compilaciones de código el código y un VSIX y, a continuación, inicia Visual Studio con ese VSIX instalado.  Al iniciar Visual Studio de esta manera, inicia con un subárbol del registro distintas para que su uso principal de Visual Studio no se verán afectado por las instancias de pruebas durante la compilación de analizadores.  La primera vez que inicie esta forma, Visual Studio realiza varios inicializaciones similares a cuando se inició por primera vez Visual Studio tras la instalación.  
  
 Cree un proyecto de consola y, a continuación, escriba el código de la matriz en el método Main de las aplicaciones de consola:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 Las líneas de código con `ImmutableArray` necesario subrayados ondulados porque es necesario obtener el paquete de NuGet inmutable y agregar un `using` instrucción en el código.  Presione el botón derecho del puntero en el nodo de proyecto en el **el Explorador de soluciones** y elija **Administrar paquetes de NuGet...**.  En el Administrador de NuGet, escriba "Invariable" en el cuadro de búsqueda y elija el elemento "System.Collections.Immutable" \(no seleccione "Microsoft.Bcl.Immutable"\) en el panel izquierdo y presione el botón instalar en el panel derecho.  Instalar el paquete, agrega una referencia a las referencias del proyecto.  
  
 Aún aparece un subrayado ondulado rojo bajo `ImmutableArray`, coloque el símbolo de intercalación en ese identificador y presione **CTRL \+.** \(punto\) para mostrar el menú de corrección sugerida y elija Agregar adecuado `using` instrucción.  
  
 **Guarde y cierre** la segunda instancia de Visual Studio por ahora a ponerlo en un estado limpio para continuar.  
  
## Finalizando el analizador utilizando Editar y continuar  
 En la primera instancia de Visual Studio, establezca un punto de interrupción al principio de su `AnalyzeObjectCreation` método presionando **F9** con el símbolo de intercalación en la primera línea.  
  
 Inicie el analizador de nuevo con **F5**, y en la segunda instancia de Visual Studio, vuelva a abrir la aplicación de consola que creó la última vez.  
  
 Volver a la primera instancia de Visual Studio en el punto de interrupción porque el compilador Roslyn vio una expresión de creación de objeto y se llama en el analizador.  
  
 **Obtiene el nodo de la creación del objeto.** Paso a través de la línea que establece el `objectCreation` variable presionando **F10**, y en el **ventana Inmediato** evaluar la expresión `“objectCreation.ToString()”`.  Verá que el nodo de sintaxis la variable apunta a es el código `"new ImmutableArray<int>()"`, simplemente lo que está buscando.  
  
 **Obtener el objeto de tipo ImmutableArray \< T \>.** Deberá comprobar si el tipo que se va a crear es ImmutableArray.  En primer lugar, obtenga el objeto que representa este tipo.  Comprobar tipos mediante el modelo semántico para asegurarse de tiene exactamente el tipo correcto y no compara la cadena de ToString\(\).  Escriba la siguiente línea de código al final de la función:  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Designar tipos genéricos en metadatos con backquotes \('\) y el número de parámetros genéricos.  Por este motivo, no se ve "... ImmutableArray \< T \> "en el nombre de metadatos.  
  
 El modelo semántico tiene muchas cosas útiles que le permiten realizar preguntas sobre los símbolos, flujo de datos, duración de la variable, etc..  Roslyn separa los nodos de sintaxis del modelo semántico por diversas razones engineering \(rendimiento, modelado código erróneo, etc.\)..  Desea que el modelo de compilación para buscar la información contenida en las referencias de comparación exacta.  
  
 Puede arrastrar el puntero de ejecución amarillo en el lado izquierdo de la ventana del editor.  Arrastre hasta la línea que establece el `objectCreation` variable y paso a paso sobre la nueva línea de código mediante **F10**.  Si sitúa el puntero del mouse sobre la variable `immutableArrayOfType`, verá que hemos encontrado el tipo exacto en el modelo semántico.  
  
 **Obtiene el tipo de la expresión de creación de objeto.** "Tipo" se utiliza en algunas formas en este artículo, pero esto significa que si tiene "Foo nuevo" expresión, debe obtener un modelo de Foo.  Debe obtener el tipo de la expresión de creación de objetos para ver si es el tipo de ImmutableArray \< T \>.  Utilizar el modelo semántico de nuevo para obtener información de símbolos para el símbolo de tipo \(ImmutableArray\) en la expresión de creación de objeto.  Escriba la siguiente línea de código al final de la función:  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Dado que el analizador debe controlar el código incompleto o incorrecto en búferes de editor \(por ejemplo, hay una falta `using` instrucción\), debe comprobar si hay `symbolInfo` está `null`.  Debe obtener un tipo con nombre \(INamedTypeSymbol\) desde el objeto de información de símbolos para finalizar el análisis.  
  
 **Comparar los tipos.** Dado que hay un tipo genérico abierto de T que estamos buscando, y el tipo en el código es un tipo genérico concreto, consultar la información de símbolos para el tipo se construye desde \(un tipo genérico abierto\) y compara ese resultado con `immutableArrayOfTType`.  Escriba lo siguiente al final del método:  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **El diagnóstico de informes.** Informes de diagnóstico es bastante fácil.  Utilice la regla que se crea en la plantilla de proyecto, que se define antes del método Initialize.  Dado que esta situación en el código es un error, puede cambiar la línea que inicializa la regla para reemplazar `DiagnosticSeverity.Warning` \(subrayado de color verde\) con `DiagnosticSeverity.Error` \(subrayado ondulado de color rojo\).  Inicializa el resto de la regla de los recursos que Editar cerca del principio del tutorial.  También necesita informar de la ubicación de la línea ondulada, que es la ubicación de la especificación de tipo de la expresión creación de objeto.  Escriba este código en el `if` bloque:  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 La función debe parecerse a esto \(que quizás un formato diferente\):  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 Quite el punto de interrupción para que pueda ver el trabajo del analizador \(y dejar de devolver a la primera instancia de Visual Studio\).  Arrastre el puntero de ejecución al principio del método y presione **F5** para continuar la ejecución.  Cuando cambie a la segunda instancia de Visual Studio, se iniciará el compilador examinar el código nuevo, y llamará a su analizador.  Puede ver una línea ondulada bajo `ImmutableType<int>`.  
  
## Agregar una "revisión de código" para el problema de código  
 Antes de comenzar, cierre la segunda instancia de Visual Studio y detener la depuración en la primera instancia de Visual Studio \(donde está desarrollando el analizador\).  
  
 **Agregue una nueva clase.** Utilice el menú contextual \(botón derecho del puntero\) en el nodo del proyecto en el Explorador de soluciones y elija Agregar un nuevo elemento.  Agregue una clase denominada `BuildCodeFixProvider`.  Esta clase debe derivarse de `CodeFixProvider`, y debe usar **CTRL \+.** \(punto\) para invocar la corrección de código que agrega el valor correcto `using` instrucción.  Esta clase también debe anotarse con `ExportCodeFixProvider` atributo y será necesario agregar un `using` instrucción para resolver el `LanguageNames` enum.  Debe tener un archivo de clase con el código siguiente en él:  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **Código auxiliar de los miembros derivados.** Ahora, colocar el símbolo de intercalación del editor en el identificador de `CodeFixProvider` y presione **CTRL \+.** \(punto\) para la implementación de esta clase base abstracta de código auxiliar.  Esto genera una propiedad y un método.  
  
 **Implemente la propiedad.** Rellene el `FixableDiagnosticIds` la propiedad `get` cuerpo con el código siguiente:  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn reúne diagnósticos y corrige mediante la coincidencia de estos identificadores, que son simplemente cadenas.  La plantilla de proyecto genera un identificador de diagnóstico, y puede cambiarlo.  El código de la propiedad sólo devuelve el identificador de la clase del analizador.  
  
 **El método RegisterCodeFixAsync toma un contexto.** El contexto es importante porque puede aplicar una revisión de código para varios diagnósticos o podría haber más de un problema en una línea de código.  Si escribe "contexto". en el cuerpo del método, la lista de finalización de Intellisense mostrará a algunos miembros útiles.  Hay un miembro de CancellationToken que puede comprobar para ver si algo desea cancelar la corrección.  Hay un miembro de documento que contiene muchos miembros útiles y le permite obtener acceso a los objetos de modelo de proyecto y solución.  Hay un miembro de intervalo que es el inicio y final de la ubicación del código especificado cuando se notifica el diagnóstico.  
  
 **Que el método sea asincrónico.** Lo primero que debe hacer es corregir la declaración del método generado para que sea un `async` \(método\).  La corrección de código de procesamiento con stub la implementación de una clase abstracta no incluye el `async` palabra clave incluso aunque el método devuelve un `Task`.  
  
 **Obtener la raíz del árbol de sintaxis.** Para modificar el código que necesario para generar un nuevo árbol de sintaxis con los cambios se realiza la corrección de código.  Necesita el `Document` desde el contexto para llamar a `GetSyntaxRootAsync`.  Se trata de un método asincrónico porque hay trabajo desconocido para obtener el árbol de sintaxis, incluidos posiblemente obtener el archivo de disco, analizarlo y generar el modelo de código de Roslyn para él.  La IU de Visual Studio debe responder durante este tiempo, donde el uso `async` permite.  Reemplace la línea de código en el método por el siguiente:  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **Busque el nodo con el problema.** Se pasan en el intervalo del contexto, pero el nodo que buscar no sea el código que se debe cambiar.  El diagnóstico notificado sólo proporciona el intervalo para el identificador de tipo \(donde la línea ondulada pertenecía\), pero tiene que reemplazar la expresión de creación de objetos completo, incluido el `new` keywoard al principio y los paréntesis al final.  Agregue el código siguiente al método \(y usar **CTRL \+.** para agregar una `using` instrucción para `ObjectCreationExpressionSyntax`\):  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **Registrar la corrección de código para la interfaz de usuario de bombilla.** Al registrar la corrección de código, Roslyn se conecta automáticamente a la interfaz de usuario de Visual Studio una bombilla.  Los usuarios finales verán que se pueden usar **CTRL \+.** \(punto\) cuando el analizador de líneas en zigzag un bad `ImmutableArray<T>` uso del constructor.  Dado que el proveedor de la revisión de código sólo se ejecuta cuando hay un problema, puede suponer que tiene la expresión de creación de objetos que estaba buscando.  Del parámetro de contexto, puede registrar la nueva corrección de código agregando el código siguiente al final de `RegisterCodeFixAsync` método:  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 Debe colocar el símbolo de intercalación del editor en el identificador `CodeAction`, a continuación, utilice **CTRL \+.** \(punto\) para agregar adecuado `using` instrucción para este tipo.  
  
 A continuación, coloque el símbolo de intercalación del editor en el `ChangeToImmutableArrayEmpty` identificador y el uso **CTRL \+.** para generar este código auxiliar de método de.  
  
 Este último fragmento de código que agregó registra la corrección de código pasando un `CodeAction` y el identificador de diagnóstico para el tipo de problema encontrado.  En este ejemplo, hay sólo una Id. de diagnóstico que este código proporciona correcciones para, por lo que puede pasar simplemente el primer elemento de la matriz de identificadores de diagnóstico.  Cuando se crea el `CodeAction`, pasa el texto que debe usar la interfaz de usuario de una bombilla como una descripción de la revisión de código.  También pasa una función que toma un CancellationToken y devuelve un nuevo documento.  El nuevo documento tiene un nuevo árbol de sintaxis que incluye el código revisado que llama `ImmutableArray.Empty`.  Este fragmento de código utiliza una expresión lambda para que pueden cerrar el nodo objectCreation y documento del contexto.  
  
 **Construir el nuevo árbol de sintaxis.** En el `ChangeToImmutableArrayEmpty` método cuyo código auxiliar que generó anteriormente, escriba la línea de código: `ImmutableArray<int>.Empty;`.  Si ver de nuevo la ventana de herramientas del visualizador de sintaxis, puede ver que esta sintaxis es un nodo de simple­memberaccessexpression.  Eso es lo que necesita este método construir y devolver un documento nuevo.  
  
 El primer cambio en `ChangeToImmutableArrayEmpty` consiste en agregar `async` antes de `Task<Document>` porque los generadores de código no se pueden suponer que el método debe ser asincrónica.  
  
 Rellene el cuerpo con el código siguiente para que el método es similar a la siguiente:  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 Tendrá que colocar el símbolo de intercalación del editor en el `SyntaxGenerator` identificador y usar **CTRL \+.** \(punto\) para agregar adecuado `using` instrucción para este tipo.  
  
 Este código usa `SyntaxGenerator`, que es un tipo muy útil para la construcción de código nuevo.  Después de obtener un generador para el documento que tiene el problema de código, `ChangeToImmutableArrayEmpty` llamadas `MemberAccessExpression`, pasando el tipo que tiene el miembro que desea tener acceso y pasando el nombre del miembro como una cadena.  
  
 A continuación, el método obtiene la raíz del documento, y dado que esto puede implicar trabajo arbitrario en el caso general, el código espera esta llamada y pasa el token de cancelación.  Modelos de código de Roslyn son inmutables, similar a trabajar con una cadena. NET; Cuando se actualiza la cadena, obtendrá un nuevo objeto de cadena de vuelta.  Cuando se llama a `ReplaceNode`, obtendrá un nuevo nodo raíz.  La mayor parte del árbol de sintaxis es compartido \(porque es inmutable\), pero la `objectCreation` nodo se reemplaza por la `memberAccess` nodo, así como todos los nodos primario hasta la raíz del árbol de sintaxis.  
  
## Probar la corrección de código  
 Ahora puede presionar **F5** para ejecutar el analizador en una segunda instancia de Visual Studio.  Abra el proyecto de consola que usó antes.  Ahora debería aparecer la bombilla donde es la nueva expresión de creación de objeto para `ImmutableArray<int>`.  Si presiona **CTRL \+.** \(punto\), verá el código corregir y verá una vista previa de diferencia de código generado automáticamente en la interfaz de usuario de bombilla.  Roslyn crea para usted.  
  
 Sugerencias de Pro: Si inicia la segunda instancia de Visual Studio y no ve la bombilla con la corrección de código, debe borrar la caché de componentes de Visual Studio.  Borrar la caché obliga a Visual Studio para volver a examinar los componentes, por lo que, a continuación, Visual Studio debe recoger el componente más reciente.  Primero, cierre la segunda instancia de Visual Studio.  A continuación, en el Explorador de Windows, vaya a su directorio user \(c:\\users\\ \< ID \>\) y busque AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\.  En este directorio, elimine el directorio de sub ComponentModelCache.  Los cambios "14" versión con Visual Studio.  
  
## Vídeo de hablar y proyectos de código de la fecha de fin  
 Puede ver este ejemplo desarrollado y se describe más detalladamente en [esta charla](http://channel9.msdn.com/events/Build/2015/3-725).  Hablar muestra el analizador de trabajo y le guiará en el proceso de compilación.  
  
 Puede ver todo el código terminado [aquí](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Las subcarpetas DoNotUseImmutableArrayCollectionInitializer y DoNotUseImmutableArrayCtor tienen un archivo de C\# para buscar problemas y un archivo de C\# que implemente las correcciones de código que aparecen en la interfaz de usuario de Visual Studio una bombilla.  Tenga en cuenta que el código terminado tiene un poco más de abstracción para evitar la obtención de una y otra vez el objeto de tipo ImmutableArray \< T \>.  Se utiliza anidada las acciones registradas para guardar el objeto de tipo en un contexto que está disponible siempre que las acciones de sub \(analizar la creación de objetos y analizar las inicializaciones de colección\) ejecutar.  
  
## Vea también  
 [Charla \\\\Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)   
 [Código completo en github](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [Varios ejemplos en github, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [Otros documentos en el sitio de github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [Reglas de FxCop implementadas con analizadores de Roslyn en github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)