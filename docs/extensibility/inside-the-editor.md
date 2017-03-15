---
title: "Dentro del Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevos: arquitectura"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# Dentro del Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor se compone de una serie de diferentes subsistemas, que están diseñados para mantener al editor de texto modelo independiente de la vista de texto y la interfaz de usuario.  
  
 Estas secciones describen los distintos aspectos del editor:  
  
-   [Información general de los subsistemas](../extensibility/inside-the-editor.md#overview)  
  
-   [El modelo de texto](../extensibility/inside-the-editor.md#textmodel)  
  
-   [La vista de texto](../extensibility/inside-the-editor.md#textview)  
  
 Estas secciones describen las características del editor:  
  
-   [Etiquetas y clasificadores](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Elementos gráficos](../extensibility/inside-the-editor.md#adornments)  
  
-   [Proyección](../extensibility/inside-the-editor.md#projection)  
  
-   [Esquematización](../extensibility/inside-the-editor.md#outlining)  
  
-   [Enlaces del mouse](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Operaciones del Editor](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Información general de los subsistemas  
  
### Subsistema de modelos de texto  
 El subsistema de modelo de texto es responsable de representar texto y lo que permite su manipulación. El subsistema de modelo de texto contiene la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz, que describe la secuencia de caracteres que se muestra en el editor. Este texto se puede modificar, supervisan y manipularse de muchas maneras. El modelo de texto también proporciona tipos para los siguientes aspectos:  
  
-   Un servicio que se asocia el texto con los archivos y administra la lectura y escribirlos en el sistema de archivos.  
  
-   Servicio de diferenciación que busca las diferencias mínimas entre las dos secuencias de objetos.  
  
-   Un sistema para describir el texto en un búfer de subconjuntos del texto de los otros búferes.  
  
 El subsistema de modelo de texto es libre de conceptos de la interfaz de usuario. Por ejemplo, no es responsable de la presentación de texto o formato de texto y no tiene ningún conocimiento de los elementos gráficos visuales que pueden estar asociados con el texto.  
  
 Los tipos públicos del subsistema de modelo de texto contenidos en Microsoft.VisualStudio.Text.Data.dll y Microsoft.VisualStudio.CoreUtilitiy.dll, que dependen sólo de la biblioteca de clases base de .NET Framework y Managed Extensibility Framework \(MEF\).  
  
### Subsistema de vista de texto  
 El subsistema de la vista de texto es responsable de dar formato y mostrar texto. Los tipos de este subsistema se dividen en dos capas, dependiendo de si los tipos se basan en Windows Presentation Foundation \(WPF\). Los tipos más importantes son <xref:Microsoft.VisualStudio.Text.Editor.ITextView> y <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, que controlan el conjunto de líneas de texto que se muestran, y también el símbolo de intercalación, la selección y los medios para etiquetar el texto mediante el uso de elementos de la UI de WPF. Este subsistema proporciona también los márgenes alrededor del texto del área de presentación. Estos márgenes se pueden extender y pueden contener distintos tipos de efectos de contenido y visuales. Ejemplos de los márgenes son línea número muestra y barras de desplazamiento.  
  
 Los tipos públicos del subsistema de la vista de texto contenidos en Microsoft.VisualStudio.Text.UI.dll y Microsoft.VisualStudio.Text.UI.Wpf.dll. El primer ensamblado contiene los elementos independientemente de la plataforma y la segunda contiene los elementos específicos de WPF.  
  
### Subsistema de clasificación  
 El subsistema de clasificación es responsable de determinar las propiedades de fuente de texto. Un clasificador divide el texto en clases diferentes, por ejemplo, "la palabra clave" o "comentario". La asignación de formato de clasificación se relaciona con estas clases a las propiedades de fuente real, por ejemplo, "Consolas azul 10 pto". Esta información se utiliza la vista de texto cuando se da formato y se representa el texto. Etiquetado, que se describe con más detalle más adelante en este tema, permite que los datos que se asociará con intervalos de texto.  
  
 Los tipos públicos del subsistema de clasificación figuran en Microsoft.VisualStudio.Text.Logic.dll y que interactúan con los aspectos visuales de clasificación, que se encuentran en Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### Subsistema de operaciones  
 El subsistema de operaciones define el comportamiento del editor. Proporciona la implementación de comandos del editor de Visual Studio y el sistema de deshacer.  
  
## Detenimiento el modelo de texto y la vista de texto  
  
###  <a name="textmodel"></a> El modelo de texto  
 El subsistema de modelo de texto consta de distintos grupos de tipos de texto. Estos incluyen el búfer de texto, instantáneas de texto y los intervalos de texto.  
  
#### Búferes de texto y las instantáneas de texto  
 El <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz representa una secuencia de caracteres Unicode que están codificados con UTF\-16, que es la codificación utilizada por el `String` tipo de .NET Framework. Puede conservar un búfer de texto como un documento de sistema de archivos, pero esto no es necesario.  
  
 El <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> se utiliza para crear un búfer de texto vacío o un búfer de texto que se inicializa desde una cadena o desde <xref:System.IO.TextReader>. El búfer de texto puede almacenarse en el sistema de archivos como un <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 El búfer de texto se puede editar cualquier subproceso hasta que un subproceso toma posesión del búfer de texto mediante una llamada a <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Después de eso, sólo ese subproceso puede realizar modificaciones.  
  
 Un búfer de texto puede ir a través de muchas versiones durante su duración. Se genera una nueva versión cada vez que se edita el búfer y un inmutable <xref:Microsoft.VisualStudio.Text.ITextSnapshot> representa el contenido de esa versión del búfer. Como instantáneas de texto son inmutables, puede tener acceso a una instantánea de texto en cualquier subproceso, sin restricciones, aunque sigue cambiando el búfer de texto que representa.  
  
#### Las instantáneas de texto y líneas de la instantánea de texto  
 Puede ver el contenido de una instantánea de texto como una secuencia de caracteres o como una secuencia de líneas. Caracteres y líneas son que ambos indizan empezando por cero. Una instantánea de texto vacío contiene cero caracteres y una línea vacía. Una línea está delimitada por cualquier secuencia de caracteres de salto de línea Unicode válido, o al principio o al final del búfer. Caracteres de salto de línea se representan explícitamente en la instantánea de texto y los saltos de línea en una instantánea de texto no tienen que ser el mismo.  
  
> [!NOTE]
>  Para obtener más información acerca de los caracteres de salto de línea en el editor de Visual Studio, consulte [Codificaciones y saltos de línea](../ide/encodings-and-line-breaks.md).  
  
 Una línea de texto se representa mediante un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objeto, que puede obtenerse a partir de una instantánea de texto para un número de línea concreto o para una posición de caracteres determinada.  
  
#### SnapshotPoints, SnapshotSpans y NormalizedSnapshotSpanCollections  
 Un <xref:Microsoft.VisualStudio.Text.SnapshotPoint> representa una posición de carácter en una instantánea. La posición se garantiza que se encuentran entre cero y la longitud de la instantánea. Un <xref:Microsoft.VisualStudio.Text.SnapshotSpan> representa un intervalo de texto en una instantánea. Su posición final se garantiza que se encuentran entre cero y la longitud de la instantánea. El <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> consta de un conjunto de <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objetos desde la misma instantánea.  
  
#### Intervalos y NormalizedSpanCollections  
 Un <xref:Microsoft.VisualStudio.Text.Span> representa un intervalo que se puede aplicar a un intervalo de texto en una instantánea de texto. Posiciones de instantánea están basadas en cero, para que intervalos pueden empezar en cualquier posición incluido cero. El `End` es igual a la suma de la propiedad de un intervalo de su `Start` propiedad y su `Length` propiedad. Un `Span` no incluye el carácter que se indiza por el `End` propiedad. Por ejemplo, un intervalo que tiene inicio \= 5 y longitud \= 3 tiene final \= 8, e incluye los caracteres en las posiciones 5, 6 y 7. La notación de este intervalo es 5..8\).  
  
 Dos intervalos de intersección si tienen todas las posiciones en común, incluidas la posición final. Por lo tanto, la intersección de \[3, 5\) y \[2, 7\) es \[3, 5\) y la intersección de \[3, 5\) y \[5, 7\) es \[5, 5\). \(Tenga en cuenta que \[5, 5\) es un intervalo vacío.\)  
  
 Dos intervalos se superponen si tienen posiciones en común, salvo la posición final. Un intervalo vacío nunca superpone a ningún otro intervalo y la superposición de dos intervalos nunca está vacía.  
  
 Un <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> es una lista de intervalos en el orden de las propiedades de inicio de los intervalos. En la lista, se combinan los intervalos contiguos o superpuestos. Por ejemplo, dado el conjunto de intervalos de \[5..9\), \[0..1\), \[3..6\), y \[9..10\), la lista normalizada de intervalos es \[0..1\), \[3..10\).  
  
#### ITextEdit, TextVersion y notificaciones de cambio de texto  
 El contenido de un búfer de texto puede cambiarse mediante una <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto. Creación de este tipo de objeto \(utilizando uno de los `CreateEdit()` métodos de <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) inicia una transacción de texto que consta de las ediciones de texto. Cada edición es un sustituto de algún intervalo de texto en el búfer mediante una cadena. Las coordenadas y el contenido de cada edición se expresan con respecto a la instantánea del búfer cuando se inició la transacción. La <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto ajusta las coordenadas de las modificaciones que se ven afectadas por otras modificaciones en la misma transacción.  
  
 Por ejemplo, considere un búfer de texto que contiene esta cadena:  
  
```  
abcdefghij  
```  
  
 Aplicar una transacción que contiene dos ediciones, una edición que reemplaza el intervalo en \[2..4\) mediante el carácter `X` y una segunda edición que reemplaza el intervalo en \[6..9\) mediante el carácter `Y`. El resultado es este búfer:  
  
```  
abXefYj  
```  
  
 Las coordenadas para la segunda edición se calcularon en relación con el contenido del búfer al principio de la transacción, antes de que se aplicó la primera edición.  
  
 Los cambios en el búfer surtirán efecto cuando el <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto se confirma llamando su `Apply()` \(método\). Si no hay al menos una edición no está vacío, un nuevo <xref:Microsoft.VisualStudio.Text.ITextVersion> se crea un nuevo <xref:Microsoft.VisualStudio.Text.ITextSnapshot> se crea y una `Changed` provoca el evento. Cada versión de texto tiene otra instantánea de texto. Una instantánea de texto representa el estado del búfer de texto completo después de una transacción de edición, pero sólo los cambios de una instantánea a la siguiente describe una versión de texto. En general, instantáneas de texto están diseñadas para utilizarse una vez y, a continuación, se descartan, mientras que las versiones de texto deben permanecer activas durante algún tiempo.  
  
 Una versión de texto contiene un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Esta colección describe los cambios que, cuando se aplica a la instantánea, se producirá la instantánea posterior. Cada <xref:Microsoft.VisualStudio.Text.ITextChange> de la colección contiene la posición del carácter de la cadena de reemplazo, el cambio y la cadena reemplazada. La cadena reemplazada está vacía para una inserción básica y la cadena de reemplazo está vacía para una eliminación básica. La colección normalizada es siempre `null` para la versión más reciente del búfer de texto.  
  
 Sólo un <xref:Microsoft.VisualStudio.Text.ITextEdit> puede crearse instancias de objeto para un búfer de texto en cualquier momento y todas las ediciones de texto deben realizarse en el subproceso que posee el búfer de texto \(si se ha reclamado la propiedad\). Se puede abandone una edición de texto mediante una llamada a su `Cancel` método o su `Dispose` método.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> También proporciona `Insert()`, `Delete()`, y `Replace()` métodos similares a los que se encuentran en el <xref:Microsoft.VisualStudio.Text.ITextEdit> interfaz. Llama a estas tiene el mismo efecto que la creación de un <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto, que realiza la llamada similar y, a continuación, aplicar la edición.  
  
#### Puntos de seguimiento y seguimiento  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> representa una posición de carácter en un búfer de texto. Si el búfer se modifica de manera que hace que la posición del carácter de desplazamiento, el punto de seguimiento se desplaza con ella. Por ejemplo, si un punto de seguimiento hace referencia a la posición 10 en un búfer y se insertarán cinco caracteres al principio del búfer, el punto de seguimiento hace referencia a la posición 15. Si se produce una inserción en con precisión la posición indicada por el punto de seguimiento, su comportamiento viene determinado por su <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, que puede ser `Positive` o `Negative`. Si el modo de seguimiento es positivo, el punto de seguimiento hace referencia al mismo carácter, que ahora está al final de la inserción; Si el modo de seguimiento es negativo, el punto de seguimiento se refiere al primer carácter insertado en la posición original. Si se elimina el carácter que ocupa la posición que se representa mediante un punto de seguimiento, el punto de seguimiento se desplaza al primer carácter que sigue el intervalo eliminado. Por ejemplo, si un punto de seguimiento hace referencia al carácter en la posición 5 y se eliminan los caracteres en las posiciones de 3 a 6, el punto de seguimiento hace referencia al carácter en la posición 3.  
  
 Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representa un intervalo de caracteres en lugar de simplemente una posición. Su comportamiento viene determinado por su <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Si el modo de seguimiento span es <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, aumenta el intervalo de seguimiento para incorporar el texto insertado en los bordes; si el modo de seguimiento span es <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, el intervalo de seguimiento no incorpora el texto insertado en sus bordes. Sin embargo, si el modo de seguimiento span es <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, una inserción inserta la posición actual hacia el inicio y si el modo de seguimiento span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, una inserción inserta la posición actual hacia el final.  
  
 Puede obtener la posición de un punto de seguimiento o el intervalo de un intervalo de seguimiento para cualquier instantánea del búfer de texto al que pertenecen. Puntos de seguimiento y los intervalos de seguimiento pueden indicarse forma segura desde cualquier subproceso.  
  
#### Tipos de contenido  
 Tipos de contenido son un mecanismo para definir tipos de contenido. Un tipo de contenido puede ser un tipo de archivo como "text", "código" o "binary" o un tipo de tecnología como "xml", "vb" o "c\#". Por ejemplo, la palabra "using" es una palabra clave en C\# y Visual Basic, pero no en otros lenguajes de programación. Por lo tanto, la definición de esta palabra clave estaría limitada a los tipos de contenido de "c\#" y "vb".  
  
 Tipos de contenido se usan como un filtro para los elementos gráficos y otros elementos del editor. Muchas características de editor y puntos de extensión se definen por tipo de contenido; Por ejemplo, color de texto es diferente para los archivos de texto sin formato, archivos XML y archivos de código fuente de Visual Basic. Búferes de texto generalmente se asignan a un tipo de contenido cuando se crean y se puede cambiar el tipo de contenido de un búfer de texto.  
  
 Tipos de contenido pueden varios\-heredar de otros tipos de contenido. El <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> permite especificar varios tipos de base como los elementos primarios de un determinado tipo de contenido.  
  
 Los desarrolladores pueden definir sus propios tipos de contenido y registrarlos mediante el <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Muchas características de editor pueden definirse con respecto a un tipo de contenido específico mediante el <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Por ejemplo, los márgenes del editor, adornos y los controladores de mouse pueden definirse para que solo se aplican a los editores que se muestran los tipos de contenido concretos.  
  
###  <a name="textview"></a> La vista de texto  
 La parte de la vista del patrón model view controller \(MVC\) define la vista de texto, el formato de la vista, los elementos gráficos, como la barra de desplazamiento y el símbolo de intercalación. Todos los elementos de presentación del editor de Visual Studio se basan en WPF.  
  
#### Vistas de texto  
 La <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaz es una representación independiente de la plataforma de una vista de texto. Se utiliza principalmente para mostrar los documentos de texto en una ventana, pero también sirve para otros fines, por ejemplo, en una información sobre herramientas.  
  
 La vista de texto hace referencia a distintos tipos de búferes de texto. El <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propiedad hace referencia a un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objeto que apunta a estos tres búferes de texto diferentes: el búfer de datos, que es el búfer de datos de nivel superior, el búfer de edición en la que la modificación se produce y el búfer visual, que es el búfer que se muestra en la vista de texto.  
  
 El texto tiene el formato en función de los clasificadores que se adjuntan en el búfer de texto subyacente y se complementa mediante el uso de los proveedores de elementos gráficos que están conectados a la propia vista de texto.  
  
#### El sistema de coordenadas de la vista de texto  
 El sistema de coordenadas de la vista de texto especifica posiciones en la vista de texto. En este sistema de coordenadas, la x valor 0,0 corresponde al borde izquierdo del texto que se muestra y el y valor 0,0 corresponde al borde superior del texto que se muestra. Los x coordinar aumenta de izquierda a derecha y los y coordinar aumenta de arriba a abajo.  
  
 Una ventanilla \(la parte de texto visible en la ventana de texto\) no se desplaza horizontalmente de la misma manera que se desplaza verticalmente. Una ventanilla se desplaza horizontalmente cambiando su coordenada izquierda para que se mueva con respecto a la superficie de dibujo. Sin embargo, se puede desplazar verticalmente cambiando el texto representado, lo que hace que una ventanilla un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.  
  
 Distancia en el sistema de coordenadas corresponde a píxeles lógicos. Si se muestra la superficie de representación de texto sin una transformación de escala, una unidad en el sistema de coordenadas de representación de texto corresponde a un píxel en la pantalla.  
  
#### Márgenes  
 El <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaz representa un margen y habilita el control de la visibilidad del margen y su tamaño. Hay cuatro márgenes predefinidos, que se denominan "Top", "Izquierda", "Right" y "Bottom" y están asociados a la parte superior, inferior, izquierdo o borde derecho de una vista. Estos márgenes son contenedores en los que se pueden colocar otros márgenes. La interfaz define métodos que devuelven el tamaño del margen y la visibilidad de un margen. Los márgenes son elementos visuales que proporcionan información adicional acerca de la vista de texto al que se adjunta. Por ejemplo, el número de línea de margen muestra números de línea para la vista de texto. El margen del glifo muestra los elementos de interfaz de usuario.  
  
 El <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz controla la creación y la colocación de los márgenes. Los márgenes se pueden ordenar con respecto a otros márgenes. Márgenes de mayor prioridad se encuentra más cerca de la vista de texto. Por ejemplo, si hay dos de los márgenes izquierdos, margen A y B del margen y margen B tiene una prioridad inferior a margen A, B de margen aparece a la izquierda del margen A.  
  
#### El Host de vista de texto  
 El <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaz contiene la vista de texto y cualquier decoraciones contiguos que acompañan a la vista, por ejemplo, las barras de desplazamiento. El host de vista de texto también contiene los márgenes que están conectados a un borde de la vista.  
  
#### Texto con formato  
 El texto que se muestra en una vista de texto se compone de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objetos. Cada línea de la vista de texto que se corresponde con una línea de texto en la vista de texto. Líneas largas en el búfer de texto subyacente se puede parcialmente oculto \(si no está habilitado el ajuste de línea\) o divididas en varias líneas de texto de la vista. El <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaz contiene métodos y propiedades para la asignación entre coordenadas y caracteres y para los elementos gráficos que pueden estar asociados a la línea.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> los objetos se crean mediante una <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfaz. Si le preocupa simplemente el texto que se muestra actualmente en la vista, puede omitir el formato de origen. Si está interesado en el formato de texto que no se muestran en la vista \(por ejemplo, para admitir texto enriquecido cortar y pegar\), puede usar <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> para dar formato al texto en un búfer de texto.  
  
 Da formato a la vista de texto uno <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> a la vez.  
  
## Características del editor  
 Las características del editor están diseñadas para que la definición de la característica es independiente de su implementación. El editor incluye estas características:  
  
-   Etiquetas y clasificadores  
  
-   Elementos gráficos  
  
-   Proyección  
  
-   Esquematización  
  
-   Enlaces del mouse y la clave  
  
-   Operaciones y primitivas  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Etiquetas y clasificadores  
 Las etiquetas son marcadores que están asociados a un intervalo de texto. Se puede presentar de maneras diferentes, por ejemplo, mediante el uso de elementos emergentes, subrayados, gráficos o colores de texto. Los clasificadores son un tipo de etiqueta.  
  
 Otros tipos de etiquetas son <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> para el texto resaltado, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> para la esquematización, y <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> para errores de compilación.  
  
#### Tipos de clasificación  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaz representa una clase de equivalencia, que es una categoría de texto abstracta. Tipos de clasificación pueden varios\-heredar de otros tipos de clasificación. Por ejemplo, las clasificaciones de lenguaje de programación puede incluir "la palabra clave", "comentario" y "identificador", que heredan de "code". Pueden incluir tipos de clasificación de lenguaje natural "sustantivo", "verbo" y "adjetivo", que se heredan de "lenguaje natural".  
  
#### Classifications  
 Una clasificación es una instancia de un tipo de clasificación determinada, normalmente en un intervalo de texto. Un <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> se utiliza para representar una clasificación. Un intervalo de clasificación puede considerarse como una etiqueta que cubre un determinado intervalo de texto y le indica al sistema que este intervalo de texto es de un tipo determinado de clasificación.  
  
#### Clasificadores  
 Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> es un mecanismo que divide el texto en un conjunto de clasificaciones. Clasificadores deben definirse para determinados tipos de contenido y crear instancias para los búferes de texto específico. Los clientes deben implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para participar en la clasificación del texto.  
  
#### Agregadores de clasificador  
 Un agregador de clasificador es un mecanismo que combina todos los clasificadores de búfer de texto en un solo conjunto de clasificaciones. Por ejemplo, un clasificador de C\# y un clasificador de idioma inglés podrían crear clasificaciones sobre un comentario en un archivo de C\#. Tenga en cuenta este comentario:  
  
```  
// This method produces a classifier  
```  
  
 Un clasificador de C\# puede etiquetar el intervalo completo como un comentario y el clasificador del idioma inglés podría clasificar "produce" como un "verbo" y "method" como un "sustantivo". El agregador genera un conjunto de clasificaciones no se superponen, y el tipo del conjunto se basa en todas las contribuciones.  
  
 Un agregador de clasificador es también un clasificador porque divide el texto en un conjunto de clasificaciones. El agregador del clasificador también garantiza que no hay ninguna superposición clasificaciones y las clasificaciones están ordenadas. Los clasificadores individuales son libertad de devolver cualquier conjunto de clasificaciones, en cualquier orden y superpuestos de ninguna manera.  
  
#### Seleccionar el color de texto y formato de clasificación  
 Formato de texto es un ejemplo de una característica que se basa en la clasificación del texto. Se usa la capa de vista de texto para determinar la presentación del texto en una aplicación. El área de formato de texto depende de WPF, pero no lo es la definición lógica de clasificaciones.  
  
 Un formato de clasificación es un conjunto de propiedades para un tipo de clasificación específica de formato. Estos formatos heredan el formato del elemento primario del tipo de clasificación.  
  
 Una <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> es una asignación de un tipo de clasificación para un conjunto de propiedades de formato de texto. La implementación de la asignación de formato en el editor controla todas las exportaciones de formatos de clasificación.  
  
###  <a name="adornments"></a> Elementos gráficos  
 Elementos gráficos son efectos gráficos que no están directamente relacionadas con la fuente y el color de los caracteres en la vista de texto. Por ejemplo, el subrayado de subrayado ondulado rojo que se utiliza para marcar el código sin compilar en muchos lenguajes de programación es un elemento de gráfico incrustado y es de información sobre herramientas emergentes adornos. Se derivan de adornos <xref:System.Windows.UIElement> e implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Dos tipos especializados de etiqueta del elemento gráfico son el <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, para los elementos gráficos que ocupan el mismo espacio que el texto en una vista, y la <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, para el subrayado de subrayado.  
  
 Elementos gráficos incrustados son gráficos que forman parte de la vista de texto con formato. Están organizados en diferentes capas del orden Z. Hay tres capas integrados, como sigue: texto, el símbolo de intercalación y la selección. Sin embargo, los desarrolladores pueden definir más capas y ponerlos en orden con respecto a ellos. Los tres tipos de elementos gráficos incrustados son opciones gráficas del texto relativo \(que mover cuando se mueve el texto y se eliminan cuando se elimina el texto\), opciones gráficas relativa de la vista \(que tienen que ver con partes no es de texto de la vista\) y adornos controlada por el propietario \(el programador debe administrar su ubicación\).  
  
 Opciones gráficas emergentes son gráficos que aparecen en una ventana pequeña encima de la vista de texto, por ejemplo, información sobre herramientas.  
  
###  <a name="projection"></a> Proyección  
 Proyección es una técnica para construir un tipo de búfer de texto que almacena el texto, pero en su lugar combina texto de otros búferes de texto diferente. Por ejemplo, se puede utilizar un búfer de proyección para concatenar el texto de los otros dos búferes y presentará el resultado como si estuviera en un único búfer, o para ocultar partes del texto en un búfer. Un búfer de proyección puede actuar como un búfer de origen a otro búfer de proyección. Puede construir un conjunto de búferes que se relacionan mediante proyección para reorganizar el texto de muchas maneras diferentes. \(Un conjunto tan también es conocido como un *gráfico de búfer*.\) La característica de esquematización de texto de Visual Studio se implementa mediante un búfer de proyección para ocultar el texto contraído y el editor de Visual Studio para páginas ASP.NET usa proyección para admitir incrustados lenguajes como Visual Basic y C\#.  
  
 Una <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> se crea mediante <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Un búfer de proyección está representado por una secuencia ordenada de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objetos que se conocen como *intervalos de origen*. El contenido de estos intervalos se presenta como una secuencia de caracteres. Los búferes de texto desde el que se dibujan los intervalos de origen se denominan *búferes de origen*. Los clientes de un búfer de proyección no tienen que tener en cuenta que es diferente de un búfer de texto normal.  
  
 El búfer de proyección escucha los eventos de cambio de texto en los búferes de origen. Cuando el texto de un origen de intervalo de cambios, el búfer de proyección asigna las coordenadas de texto cambiado a sus propio coordenadas y genera eventos de cambio de texto adecuado. Por ejemplo, considere la posibilidad de búferes de origen A y B que tienen este contenido:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Si el búfer de proyección P está formado de dos intervalos de texto, una que tenga todos de búfer y el otro que todas búfer B, P tiene el siguiente contenido:  
  
```  
P: ABCDEvwxyz  
```  
  
 Si la subcadena `xy` se elimina del búfer B, entonces el búfer P genera un evento que indica que se eliminaron los caracteres en posiciones 7 y 8.  
  
 También se puede editar directamente el búfer de proyección. Propaga las modificaciones de los búferes de origen correspondiente. Por ejemplo, si se inserta una cadena en el búfer P en la posición 6 \(la posición original del carácter "v"\), la inserción se propaga al búfer de B en la posición 1.  
  
 Hay restricciones en los intervalos de origen que contribuyen a un búfer de proyección. No se pueden superponer intervalos de origen; una ubicación en un búfer de proyección no puede asignar a más de una ubicación en cualquier búfer de origen y una ubicación en un búfer de origen no se puede asignar a más de una ubicación en un búfer de proyección. No circularities se permiten en la relación de búfer de origen.  
  
 Los eventos se producen cuando el conjunto de código fuente almacena en búfer cambia de un búfer de proyección y cuando el conjunto de origen abarca los cambios.  
  
 Un búfer de elisión es un tipo especial de búfer de proyección. Se utiliza principalmente para la esquematización y para las operaciones que expandir y contraer bloques de texto. Un búfer de elisión se basa en un solo búfer de origen y los intervalos en el búfer de elisión se deben ordenar los mismos como se ordenan en el búfer de origen.  
  
##### El gráfico de búfer  
 El <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaz permite la asignación entre un gráfico de los búferes de proyección. Todos los búferes de texto y los búferes de proyección se recopilan en un gráfico acíclico dirigido, al igual que el árbol de sintaxis abstracta que se genera mediante un compilador de lenguaje. El gráfico se define mediante el búfer superior, que puede ser cualquier búfer de texto. El gráfico de búfer puede asignar desde un punto en el búfer superior a un punto en un búfer de origen, o desde un intervalo en el búfer superior a un conjunto de intervalos en un búfer de origen. De forma similar, puede asignar un punto o abarcan desde un búfer de origen hasta un punto en el búfer superior. Gráficos de búfer se crean mediante el <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### Eventos y los búferes de proyección  
 Cuando se modifica un búfer de proyección, las modificaciones se envían desde el búfer de proyección a los búferes que dependen de él. Después de modifican todos los búferes, se provocan eventos de cambio de búfer, comenzando por el búfer más profundo.  
  
###  <a name="outlining"></a> Esquematización  
 Esquematización es la capacidad para expandir o contraer diferentes bloques de texto en una vista de texto. Esquematización se define como una especie de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, de la misma manera que se definen opciones gráficas. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> es una etiqueta que define un área de texto que puede expandir o contraer. Para utilizar un esquema, debe importar el <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> para obtener un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. El Administrador de esquematización enumera, contrae y expande los distintos bloques, que se representan como <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objetos y genera eventos en consecuencia.  
  
###  <a name="mousebindings"></a> Enlaces del mouse  
 Enlaces del mouse vinculan movimientos del mouse a diferentes comandos. Enlaces del mouse se definen mediante un <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, y los enlaces de teclado se definen mediante un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. El <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automáticamente crea instancias de todos los enlaces y se conectan a los eventos del mouse en la vista.  
  
 El <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaz contiene controladores de eventos de procesamiento previo y posterior al proceso para los distintos eventos de mouse. Controlador de uno de los eventos, puede invalidar algunos de los métodos de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Operaciones del Editor  
 Las operaciones del editor se pueden usar para automatizar la interacción con el editor de secuencias de comandos u otros fines. Puede importar el <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> a las operaciones de acceso en un determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. A continuación, puede utilizar estos objetos para modificar la selección, desplácese a la vista o mover el símbolo de intercalación a diferentes partes de la vista.  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense es compatible con las bombillas, ayuda para las firmas \(también conocido como información de parámetros\), información rápida y finalización de instrucciones.  
  
 Finalización de instrucciones proporciona listas emergentes de finalización potenciales para los nombres de método, los elementos XML y otros elementos de código o marcado. En general, un gesto del usuario invoca una sesión de finalización. La sesión muestra la lista de finalizaciones posibles, y el usuario puede seleccionar uno o descartar la lista. El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> es responsable de crear y activar el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcula el <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> de elementos de la finalización de la sesión.  
  
## Vea también  
 [Servicio de lenguaje y los puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Editor de importaciones](../extensibility/editor-imports.md)