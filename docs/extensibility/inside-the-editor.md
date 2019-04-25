---
title: Dentro del editor
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3979138944671ff2809f4f73beb0a28b222ec5ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053200"
---
# <a name="inside-the-editor"></a>Dentro del editor

El editor se compone de varios subsistemas distintos, que están diseñados para mantener al editor de texto modelo independiente de la vista de texto y la interfaz de usuario.

Estas secciones describen distintos aspectos del editor:

- [Información general de los subsistemas](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [El modelo de texto](../extensibility/inside-the-editor.md#the-text-model)

- [La vista de texto](../extensibility/inside-the-editor.md#the-text-view)

Estas secciones describen las características del editor:

- [Las etiquetas y clasificadores](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Elementos gráficos](../extensibility/inside-the-editor.md#adornments)

- [Proyección](../extensibility/inside-the-editor.md#projection)

- [Esquematización](../extensibility/inside-the-editor.md#outlining)

- [Enlaces del mouse](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operaciones de editor](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Información general de los subsistemas

### <a name="text-model-subsystem"></a>Subsistema de modelos de texto

El subsistema de modelo de texto es responsable de representar texto y lo que permite su manipulación. El subsistema de modelo de texto contiene la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz, que describe la secuencia de caracteres que se va a mostrar el editor. Este texto se puede modificar, supervisan y manipularse en muchos sentidos. El modelo de texto también proporciona tipos para los siguientes aspectos:

- Un servicio que se asocia el texto con archivos y administra la lectura y escribirlos en el sistema de archivos.

- Un servicio de diferenciación que busca las diferencias mínimas entre las dos secuencias de objetos.

- Un sistema para describir el texto en un búfer de subconjuntos del texto de otros búferes.

El subsistema de modelo de texto es libre de conceptos de la interfaz de usuario. Por ejemplo, no es responsable del diseño de texto o formato de texto y no tiene ningún conocimiento de los elementos gráficos visuales que pueden estar asociados con el texto.

Los tipos públicos del subsistema de modelo de texto se encuentran en *Microsoft.VisualStudio.Text.Data.dll* y *Microsoft.VisualStudio.CoreUtility.dll*, que dependa únicamente de la base de .NET Framework biblioteca de clases y Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Subsistema de la vista de texto

El subsistema de la vista de texto es responsable de mostrar texto y formato. Los tipos de este subsistema se dividen en dos capas, dependiendo de si los tipos se basan en Windows Presentation Foundation (WPF). Los tipos más importantes son <xref:Microsoft.VisualStudio.Text.Editor.ITextView> y <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, que controlan el conjunto de líneas de texto que se muestran y también el símbolo de intercalación, la selección y las facilidades para adornar el texto mediante el uso de los elementos de UI de WPF. Este subsistema también proporciona el área de presentación de los márgenes alrededor del texto. Estos márgenes se pueden ampliar y pueden contener diferentes tipos de efectos de contenido y visuales. Ejemplos de los márgenes son línea número muestra y barras de desplazamiento.

Los tipos públicos del subsistema de vista de texto que se encuentran en *Microsoft.VisualStudio.Text.UI.dll* y *Microsoft.VisualStudio.Text.UI.Wpf.dll*. El primer ensamblado contiene los elementos independientes de la plataforma y la segunda contiene los elementos específicos de WPF.

### <a name="classification-subsystem"></a>Subsistema de clasificación

El subsistema de clasificación es responsable de determinar las propiedades de fuente de texto. Un clasificador divide el texto en clases diferentes, por ejemplo, "palabra clave" o "comment". La asignación de formato de clasificación se relaciona con estas clases a las propiedades de fuente real, por ejemplo, "Consolas azul 10pt". Esta información se usa la vista de texto cuando se da formato y representa el texto. Etiquetado, que se describe con más detalle más adelante en este tema, permite que los datos que se asociará con intervalos de texto.

Los tipos públicos del subsistema de clasificación se encuentran en Microsoft.VisualStudio.Text.Logic.dll, y que interactúan con los aspectos visuales de clasificación, que se encuentran en Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Subsistema de operaciones

El subsistema de operaciones define el comportamiento del editor. Proporciona la implementación de comandos del editor de Visual Studio y el sistema de deshacer.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Detenimiento el modelo de texto y la vista de texto

### <a name="the-text-model"></a>El modelo de texto

El subsistema de modelo de texto consta de diferentes agrupaciones de tipos de texto. Estos incluyen el búfer de texto, las instantáneas de texto y los intervalos de texto.

#### <a name="text-buffers-and-text-snapshots"></a>Los búferes de texto y las instantáneas de texto

El <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz representa una secuencia de caracteres Unicode que están codificados con UTF-16, que es la codificación utilizado por el `String` tipo en .NET Framework. Un búfer de texto puede almacenarse como un documento de archivo del sistema, pero esto no es necesario.

El <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> se utiliza para crear un búfer de texto vacío o un búfer de texto que se inicializa desde una cadena o desde <xref:System.IO.TextReader>. El búfer de texto puede conservarse en el sistema de archivos como un <xref:Microsoft.VisualStudio.Text.ITextDocument>.

Cualquier subproceso puede editar el búfer de texto hasta que un subproceso toma posesión del búfer de texto mediante una llamada a <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Después de eso, sólo ese subproceso puede realizar modificaciones.

Un búfer de texto puede ir a través de muchas versiones durante su vigencia. Se genera una nueva versión cada vez que se edita el búfer y un inmutable <xref:Microsoft.VisualStudio.Text.ITextSnapshot> representa el contenido de esa versión del búfer. Dado que las instantáneas de texto son inmutables, puede tener acceso a una instantánea de texto en cualquier subproceso, sin restricciones, incluso si el búfer de texto que representa sigue cambiando.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantáneas de texto y líneas de la instantánea de texto

Puede ver el contenido de una instantánea de texto como una secuencia de caracteres o como una secuencia de líneas. Los caracteres y líneas son que ambos indizan empezando por cero. Una instantánea de texto vacío contiene cero caracteres y una línea vacía. Una línea está delimitada por cualquier secuencia de caracteres de salto de línea Unicode válido, o por el principio o al final del búfer. Caracteres de salto de línea se representan explícitamente en la instantánea de texto y los saltos de línea en una instantánea de texto no tienen que ser el mismo.

> [!NOTE]
> Para obtener más información sobre los caracteres de salto de línea en el editor de Visual Studio, consulte [codificaciones y saltos de línea](../ide/encodings-and-line-breaks.md).

Una línea de texto se representa mediante un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objeto, que puede obtenerse a partir de una instantánea de texto para un número de línea concreto o para una posición de caracteres determinada.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Elementos SnapshotPoint SnapshotSpans y NormalizedSnapshotSpanCollections

Un <xref:Microsoft.VisualStudio.Text.SnapshotPoint> representa una posición de carácter en una instantánea. La posición se garantiza que se encuentran entre cero y la longitud de la instantánea. Un <xref:Microsoft.VisualStudio.Text.SnapshotSpan> representa un intervalo de texto en una instantánea. Su posición final garantiza que se encuentran entre cero y la longitud de la instantánea. El <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> consta de un conjunto de <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objetos desde la misma instantánea.

#### <a name="spans-and-normalizedspancollections"></a>Intervalos y NormalizedSpanCollections

Un <xref:Microsoft.VisualStudio.Text.Span> representa un intervalo que se puede aplicar a un intervalo de texto en una instantánea de texto. Las posiciones de instantánea son de base cero, para que intervalos pueden empezar en cualquier posición incluida cero. El `End` propiedad de un intervalo es igual a la suma de sus `Start` propiedad y su `Length` propiedad. Un `Span` no incluye el carácter que se indiza por el `End` propiedad. Por ejemplo, un intervalo que tiene inicio = 5 y longitud = 3 ih = 8, e incluye los caracteres en las posiciones 5, 6 y 7. La notación de este intervalo es 5..8).

Dos intervalos forman una intersección si tienen todas las posiciones en común, incluida la posición final. Por lo tanto, la intersección de [3, 5) y [2, 7) es [3, 5) y la intersección de [3, 5) y [5, 7) es [5, 5). (Tenga en cuenta que [5, 5) es un intervalo vacío.)

Dos intervalos se superponen si tienen posiciones en común, salvo la posición final. Un intervalo vacío nunca se superpone a ningún otro intervalo, y la superposición de dos intervalos nunca está vacía.

Un <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> es una lista de intervalos en el orden de las propiedades de inicio de los intervalos. En la lista, se combinan los intervalos contiguos o superpuestos. Por ejemplo, dado el conjunto de intervalos [5..9), [0..1), [3..6), y [9..10), la lista normalizada de intervalos es [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notificaciones de cambio ITextEdit, TextVersion y texto

Se puede cambiar el contenido de un búfer de texto mediante un <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto. Creación de este tipo de objeto (mediante uno de los `CreateEdit()` métodos de <xref:Microsoft.VisualStudio.Text.ITextBuffer>) inicia una transacción de texto que consta de las ediciones de texto. Cada edición es un sustituto de algún intervalo de texto en el búfer mediante una cadena. Las coordenadas y el contenido de cada edición se expresan con respecto a la instantánea del búfer cuando se inició la transacción. La <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto ajusta las coordenadas de las modificaciones que se ven afectadas por otras modificaciones en la misma transacción.

Por ejemplo, considere la posibilidad de un búfer de texto que contiene esta cadena:

```
abcdefghij
```

Aplicar una transacción que contiene dos ediciones, una edición que reemplaza el intervalo en [2..4) mediante el carácter `X` y una segunda edición que reemplaza el intervalo en [6..9) mediante el carácter `Y`. El resultado es este búfer:

```
abXefYj
```

Las coordenadas para la segunda edición se calcularon en relación con el contenido del búfer al principio de la transacción, antes de aplica la primera edición.

Los cambios en el búfer surtirán efecto cuando el <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto se confirma llamando su `Apply()` método. Si se produjo al menos una edición no vacío, un nuevo <xref:Microsoft.VisualStudio.Text.ITextVersion> se crea un nuevo <xref:Microsoft.VisualStudio.Text.ITextSnapshot> se crea y uno `Changed` provoca el evento. Cada versión de texto tiene otra instantánea de texto. Una instantánea de texto representa el estado del búfer de texto completo después de una transacción de edición, pero solo los cambios de una instantánea a la siguiente describe una versión de texto. En general, instantáneas de texto están diseñadas para usarse una vez y, a continuación, se descartan, mientras que las versiones de texto deben permanecer activas durante algún tiempo.

Una versión de texto contiene un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Esta colección describe los cambios que, cuando se aplica a la instantánea, generar la instantánea posteriores. Cada <xref:Microsoft.VisualStudio.Text.ITextChange> en la colección contiene la posición del carácter de la cadena de reemplazo, el cambio y la cadena reemplazada. La cadena reemplazada está vacía para una inserción básica y la cadena de reemplazo está vacía para una eliminación básica. La colección normalizada es siempre `null` para la versión más reciente del búfer de texto.

Solo un <xref:Microsoft.VisualStudio.Text.ITextEdit> pueden crearse instancias para un búfer de texto en cualquier momento y se deben realizar todas las ediciones de texto en el subproceso que posee el búfer de texto (si la propiedad se haya solicitado). Edición de texto puede abandonarse mediante una llamada a su `Cancel` método o su `Dispose` método.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> También proporciona `Insert()`, `Delete()`, y `Replace()` métodos similares a los que se encuentran en el <xref:Microsoft.VisualStudio.Text.ITextEdit> interfaz. Llama a estas tiene el mismo efecto que la creación de un <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto, que realiza la llamada similar y, a continuación, aplicar la edición.

#### <a name="tracking-points-and-tracking-spans"></a>Puntos de seguimiento y los intervalos de seguimiento

Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> representa una posición de carácter en un búfer de texto. Si se edita el búfer de forma que hace que la posición del carácter que se va a desplazar, desplaza el punto de seguimiento con él. Por ejemplo, si un punto de seguimiento hace referencia a la posición 10 en un búfer y se insertarán cinco caracteres al principio del búfer, el punto de seguimiento, a continuación, hace referencia posición 15. Si se produce una inserción con precisión la posición indicada por el punto de seguimiento, su comportamiento viene determinada por su <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, que puede ser `Positive` o `Negative`. Si el modo de seguimiento es positivo, el punto de seguimiento hace referencia al mismo carácter, que ahora está al final de la inserción. Si el modo de seguimiento es negativo, el punto de seguimiento hace referencia al primer carácter insertado en la posición original. Si se elimina el carácter que ocupa la posición que se representa mediante un punto de seguimiento, el punto de seguimiento se desplaza al primer carácter que sigue el intervalo se eliminó. Por ejemplo, si hace referencia un punto de seguimiento para el carácter que ocupa la posición 5 y se eliminan los caracteres en posiciones 3 a 6, el punto de seguimiento hace referencia el carácter que ocupa la posición 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representa un intervalo de caracteres en lugar de simplemente una posición. Su comportamiento viene determinada por su <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Si es el modo de seguimiento span [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), aumenta el intervalo de seguimiento para incorporar el texto insertado en sus bordes. Si es el modo de seguimiento span [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), el intervalo de seguimiento no incorpora texto insertado en sus bordes. Sin embargo, si es el modo de seguimiento span [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), una inserción inserta la posición actual hacia el inicio, y si es el modo de seguimiento span [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), un inserción inserta la posición actual hacia el final.

Puede obtener la posición de un punto de seguimiento o el intervalo de un intervalo de seguimiento para cualquier instantánea del búfer de texto al que pertenecen. Puntos de seguimiento y los intervalos de seguimiento pueden referenciarse de forma segura desde cualquier subproceso.

#### <a name="content-types"></a>Tipos de contenido

Tipos de contenido son un mecanismo para definir los distintos tipos de contenido. Un tipo de contenido puede ser un tipo de archivo, como "text", "code" o "binary" o un tipo de tecnología, como "xml", "vb" o "c#". Por ejemplo, la palabra "using" es una palabra clave en C# y Visual Basic, pero no en otros lenguajes de programación. Por lo tanto, la definición de esta palabra clave estaría limitada a los tipos de contenido de "c#" y "vb".

Tipos de contenido se usan como un filtro para los elementos gráficos y otros elementos del editor. Muchas de las características del editor y puntos de extensión se definen por cada tipo de contenido. Por ejemplo, color de texto es diferente para los archivos de texto sin formato, archivos XML y archivos de código fuente de Visual Basic. Los búferes de texto normalmente se asignan a un tipo de contenido cuando se crean y se puede cambiar el tipo de contenido de un búfer de texto.

Tipos de contenido pueden varios-heredar de otros tipos de contenido. El <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> le permite especificar varios tipos bases como los elementos primarios de un determinado tipo de contenido.

Los desarrolladores pueden definir sus propios tipos de contenido y registrarlos mediante el <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Muchas características del editor se pueden definir con respecto a un tipo de contenido específico mediante el uso de la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Por ejemplo, se pueden definir márgenes del editor, los elementos gráficos y controladores de mouse para que se apliquen solo a los editores que se muestran los tipos de contenido concretos.

### <a name="the-text-view"></a>La vista de texto

El elemento de vista del modelo vista controlador (MVC) define la vista de texto, el formato de la vista, los elementos gráficos, como la barra de desplazamiento y el símbolo de intercalación. Todos los elementos de presentación del editor de Visual Studio se basan en WPF.

#### <a name="text-views"></a>Vistas de texto

El <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaz es una representación independiente de la plataforma de una vista de texto. Se utiliza principalmente para mostrar los documentos de texto en una ventana, pero también sirve para otros fines, por ejemplo, en una información sobre herramientas.

La vista de texto hace referencia a tipos diferentes de los búferes de texto. El <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propiedad hace referencia a un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objeto que apunta a estos tres búferes de texto diferentes: el búfer de datos, que es el búfer de datos de nivel superior, el búfer de edición, en que la modificación se produce y el búfer visual, que es el búfer que es se muestra en la vista de texto.

El texto tiene el formato en función de los clasificadores que están conectados en el búfer de texto subyacente y se complementa mediante el uso de los proveedores de elemento gráfico que están asociados a la propia vista de texto.

#### <a name="the-text-view-coordinate-system"></a>El sistema de coordenadas de la vista de texto

El sistema de coordenadas de la vista de texto especifica posiciones en la vista de texto. En este sistema de coordenadas, el valor de x 0,0 corresponde al borde izquierdo del texto que se muestra y el valor y 0,0 corresponde al borde superior del texto que se muestra. La coordenada x aumenta de izquierda a derecha, y aumenta la coordenada y de arriba a abajo.

Una ventanilla (la parte del texto visible en la ventana de texto) no se desplaza horizontalmente en la misma manera como se desplaza verticalmente. Una ventanilla se desplaza horizontalmente cambiando su coordenada izquierda para que se mueva con respecto a la superficie de dibujo. Sin embargo, se puede desplazar verticalmente cambiando el texto representado, lo que hace que una ventanilla de una <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.

Las distancias en el sistema de coordenadas se corresponden con píxeles lógicos. Si se muestra la superficie de representación de texto sin una transformación de escala, una unidad en el sistema de coordenadas de representación de texto corresponde a un píxel en la pantalla.

#### <a name="margins"></a>Márgenes

El <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaz representa un margen y le permite controlar la visibilidad de los márgenes y su tamaño. Hay cuatro márgenes predefinidos, que se denominan "Top", "Left", "Right" y "Bottom" y están asociados a la parte superior, inferior, izquierdo o borde derecho de una vista. Estos márgenes son contenedores en el que se pueden colocar otros márgenes. La interfaz define métodos que devuelven el tamaño del margen y la visibilidad de un margen. Los márgenes son elementos visuales que proporcionan información adicional acerca de la vista de texto a los que están conectados. Por ejemplo, el margen del número de línea muestra números de línea para la vista de texto. El margen del glifo muestra los elementos de interfaz de usuario.

El <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz controla la creación y selección de ubicación de los márgenes. Los márgenes se pueden ordenar con respecto a otros márgenes. Los márgenes de mayor prioridad se encuentra más cerca de la vista de texto. Por ejemplo, si hay dos de los márgenes izquierdos, margen A y B de margen y margen B tiene una prioridad inferior a un margen, margen B aparece a la izquierda del margen A.

#### <a name="the-text-view-host"></a>El host de vista de texto

El <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaz contiene la vista de texto y cualquier decoraciones contiguos que acompañan a la vista, por ejemplo, las barras de desplazamiento. El host de vista de texto contiene también los márgenes que están asociados a un borde de la vista.

#### <a name="formatted-text"></a>Texto con formato

El texto que se muestra en una vista de texto se compone de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objetos. Cada línea de la vista de texto corresponde a una línea de texto en la vista de texto. Las líneas largas en el búfer de texto subyacente pueden parcialmente oculto (si no está habilitado el ajuste de líneas) o divididas en varias líneas de la vista de texto. El <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaz contiene métodos y propiedades para la asignación entre las coordenadas y caracteres y para los elementos gráficos que pueden estar asociados con la línea.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> los objetos se crean mediante un <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfaz. Si le preocupa simplemente el texto que se muestra actualmente en la vista, puede omitir el origen de formato. Si está interesado en el formato de texto que no se muestra en la vista (por ejemplo, admite texto enriquecido cortar y pegar), puede usar <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> para dar formato al texto en un búfer de texto.

Da formato a la vista de texto uno <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> a la vez.

## <a name="editor-features"></a>Características del editor

Las características del editor están diseñadas para que la definición de la característica es independiente de su implementación. El editor incluye estas características:

- Las etiquetas y clasificadores

- Elementos gráficos

- Proyección

- esquematizar

- Enlaces del mouse y la clave

- Las operaciones y primitivas

- IntelliSense

### <a name="tags-and-classifiers"></a>Las etiquetas y clasificadores

Las etiquetas son marcadores que están asociados con un intervalo de texto. Se puede presentar de maneras diferentes, por ejemplo, mediante el uso de colores de texto, subrayados, gráficos o elementos emergentes. Los clasificadores son un tipo de etiqueta.

Otros tipos de etiquetas son <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> para texto resaltado, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> para la esquematización, y <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> para errores de compilación.

#### <a name="classification-types"></a>Tipos de clasificación

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaz representa una clase de equivalencia, que es una categoría abstracta de texto. Tipos de clasificación pueden varios-heredar de otros tipos de clasificación. Por ejemplo, las clasificaciones de lenguaje de programación puede incluir "palabra clave", "comment" e "identificador", que se heredan de "code". Pueden incluir tipos de clasificación de lenguaje natural "sustantivo", "verbo" y "adjetivo", que se heredan de "lenguaje natural".

#### <a name="classifications"></a>Classifications

Una clasificación es una instancia de un tipo de clasificación determinada, normalmente a través de un intervalo de texto. Un <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> se utiliza para representar una clasificación. Un intervalo de clasificación puede considerarse como una etiqueta que se trata de un determinado intervalo de texto y le indica al sistema que este intervalo de texto es de un tipo de clasificación determinado.

#### <a name="classifiers"></a>Clasificadores

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> es un mecanismo que divide el texto en un conjunto de clasificaciones. Clasificadores deben definirse para determinados tipos de contenido y crea una instancia para los búferes de texto específico. Los clientes deben implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para participar en la clasificación de texto.

#### <a name="classifier-aggregators"></a>Agregadores de clasificador

Un agregador del clasificador es un mecanismo que combina todos los clasificadores de búfer de texto de uno en un solo conjunto de clasificaciones. Por ejemplo, un clasificador de C# y un clasificador de idioma inglés pueden crear clasificaciones a través de un comentario en un archivo de C#. Tenga en cuenta este comentario:

```
// This method produces a classifier
```

Un clasificador de C# podría etiquetar el intervalo completo como un comentario y el clasificador del idioma inglés podría clasificar "genera" como un "verbo" y "method" como un "sustantivo". El agregador genera un conjunto de clasificaciones no se superponen y se basa el tipo del conjunto de todas las contribuciones.

Un agregador del clasificador es también un clasificador porque divide el texto en un conjunto de clasificaciones. El agregador del clasificador también garantiza que no hay ningún clasificaciones que se superponen y que se ordenan las clasificaciones. Clasificadores individuales son libertad de devolver cualquier conjunto de clasificaciones, en cualquier orden y que se superponen en modo alguno.

#### <a name="classification-formatting-and-text-coloring"></a>Formato de clasificación y el color de texto

Formato de texto es un ejemplo de una característica que se basa en la clasificación de texto. Se está usando la capa de vista de texto para determinar la presentación del texto en una aplicación. El área de formato de texto depende de WPF, pero no la definición lógica de clasificaciones.

Un formato de clasificación es un conjunto de propiedades para un tipo de clasificación específica de formato. Estos formatos heredan el formato del elemento primario del tipo de clasificación.

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> es un mapa de un tipo de clasificación para un conjunto de propiedades de formato de texto. La implementación de la asignación de formato en el editor controla todas las exportaciones de formatos de clasificación.

### <a name="adornments"></a>Elementos gráficos

Los elementos gráficos son efectos gráficos que no están directamente relacionadas con la fuente y color de los caracteres en la vista de texto. Por ejemplo, el subrayado de subrayado ondulado de color rojo que se usa para marcar el código sin compilar en muchos lenguajes de programación es un elemento de gráfico incrustado e informaciones sobre herramientas son ventanas emergentes adornos. Se derivan de los elementos gráficos <xref:System.Windows.UIElement> e implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Dos tipos especializados de etiqueta del elemento gráfico son el <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, los elementos gráficos que ocupan el mismo espacio que el texto en una vista, y el <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, para el subrayado de subrayado ondulado de color.

Elementos gráficos incrustados son gráficos que forman parte de la vista de texto con formato. Están organizados en niveles diferentes de orden Z. Hay tres capas integradas, como sigue: texto, el símbolo de intercalación y la selección. Sin embargo, los desarrolladores pueden definir más capas y colocarlos en orden con respecto a ellos. Los tres tipos de elementos gráficos incrustados son elementos gráficos del texto relativo (que mover cuando el texto se mueve y se eliminan cuando se elimina el texto), relativa a la vista de los elementos gráficos, (que tienen que ver con los elementos que no sean de texto de la vista) y controlado por el propietario de los elementos gráficos (los programador debe administrar su ubicación).

Elementos gráficos emergentes son gráficos que aparecen en una ventana pequeña encima de la vista de texto, por ejemplo, información sobre herramientas.

### <a name="projection"></a> Proyección

Proyección es una técnica para construir un tipo de búfer de texto que no almacena realmente el texto, pero en su lugar, combina el texto de otros búferes de texto diferente. Por ejemplo, puede usarse un búfer de proyección para concatenar el texto de los otros dos búferes y presentará el resultado como si se encuentra en un solo búfer, o para ocultar partes del texto en un búfer. Un búfer de proyección puede actuar como un búfer de origen a otro búfer de proyección. Para reorganizar el texto de muchas maneras diferentes, se puede construir un conjunto de búferes que se relacionan mediante la proyección. (Un conjunto de este tipo es también se denomina un *gráfico de búfer*.) La característica de esquematización del texto de Visual Studio se implementa mediante el uso de un búfer de proyección para ocultar el texto contraído y el editor de Visual Studio para las páginas ASP.NET usa proyección para admitir incrustados lenguajes como Visual Basic y C#.

Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> se crea mediante <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Un búfer de proyección se representa mediante una secuencia ordenada de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objetos que se conocen como *intervalos de origen*. El contenido de estos intervalos se presenta como una secuencia de caracteres. Los búferes de texto desde el que se dibujan los intervalos de origen se denominan *búferes de origen*. Los clientes de un búfer de proyección no es necesario tener en cuenta que difiere un búfer de texto normales.

El búfer de proyección escucha los eventos de cambio de texto en los búferes de origen. Cuando el texto de un origen de abarcar los cambios, el búfer de proyección asigna las coordenadas de texto cambiado a su propio coordenadas y genera eventos de cambio de texto adecuado. Por ejemplo, considere la posibilidad de búferes de origen A y B que tienen estos contenidos:

```
A: ABCDE
B: vwxyz
```

Si el búfer de proyección P se forma a partir de dos intervalos de texto, una que tiene todas de búfer y la otra que tenga todos del búfer de B, P tiene el siguiente contenido:

```
P: ABCDEvwxyz
```

Si la subcadena `xy` se elimina del búfer B, entonces el búfer P provoca un evento que indica que se eliminaron los caracteres en posiciones 7 y 8.

También se puede editar directamente el búfer de proyección. Propaga las modificaciones realizadas en los búferes de origen adecuado. Por ejemplo, si se inserta una cadena en el búfer P en la posición 6 (la posición original del carácter "v"), la inserción se propaga al búfer de B en la posición 1.

Hay restricciones en los intervalos de origen que contribuyen a un búfer de proyección. No se pueden superponer intervalos de origen; una ubicación en un búfer de proyección no puede asignar a más de una ubicación en cualquier búfer de origen y una ubicación en un búfer de origen no puede asignar a más de una ubicación en un búfer de proyección. No hay circularities se permiten en la relación de búfer de origen.

Los eventos se producen cuando el conjunto de código fuente almacena en búfer para cambia de un búfer de proyección y cuando el conjunto de origen abarca los cambios.
Un búfer de elisión es un tipo especial de búfer de proyección. Se utiliza principalmente para la esquematización y para las operaciones que expandir y contraer bloques de texto. Un búfer de elisión se basa en un solo búfer de origen y los intervalos en el búfer de elisión se deben ordenar el mismo como están ordenadas en el búfer de origen.

#### <a name="the-buffer-graph"></a>El gráfico del búfer

El <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaz permite la asignación entre un gráfico de búferes de proyección. Todos los búferes de texto y los búferes de proyección se recopilan en un gráfico acíclico dirigido, igual que el árbol de sintaxis abstracta que se genera mediante un compilador de lenguaje. El gráfico se define mediante el búfer superior, que puede ser cualquier búfer de texto. El gráfico del búfer se puede asignar desde un punto en el búfer superior a un punto en un búfer de origen, o desde un intervalo en el búfer superior a un conjunto de intervalos en un búfer de origen. De forma similar, puede asignar un punto o abarcan desde un búfer de origen a un punto en el búfer superior. Gráficos de búfer se crean mediante el <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.

#### <a name="events-and-projection-buffers"></a>Eventos y los búferes de proyección

Cuando se modifica un búfer de proyección, las modificaciones se envían desde el búfer de proyección a los búferes que dependen de él. Después de que todos los búferes se modifican, se generan eventos de cambio de búfer, empezando por el búfer más profundo.

### <a name="outlining"></a>esquematizar

Esquematización es la capacidad para expandir o contraer diferentes bloques de texto en una vista de texto. Esquematización se define como una especie de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, en la misma manera que se definen los elementos gráficos. Un <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> es una etiqueta que se define una región de texto que puede expandir o contraer. Para utilizar un esquema, debe importar el <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> para obtener un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Enumera el Administrador de esquematización, se contrae y expande los bloques diferentes, que se representan como <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objetos y genera eventos en consecuencia.

### <a name="mouse-bindings"></a>Enlaces del mouse

Los enlaces del mouse vinculan movimientos del mouse a distintos comandos. Los enlaces del mouse se definen mediante un <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, y los enlaces de teclado se definen mediante un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. El <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automáticamente crea una instancia de todos los enlaces y los conecta a los eventos del mouse en la vista.

El <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaz contiene controladores de eventos de procesamiento previo y posterior al proceso para los distintos eventos de mouse. Controlador de uno de los eventos, puede invalidar algunos de los métodos en <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.

### <a name="editor-operations"></a>Operaciones de editor

Operaciones de editor pueden utilizarse para automatizar la interacción con el editor de secuencias de comandos u otros fines. Puede importar el <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> a las operaciones de acceso en un determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. A continuación, puede usar estos objetos para modificar la selección, desplazar la vista o mover el símbolo de intercalación a diferentes partes de la vista.

### <a name="intellisense"></a>IntelliSense

IntelliSense es compatible con las bombillas, información rápida, ayuda para la firma (también conocido como información de parámetros) y finalización de instrucciones.

Finalización de instrucciones proporciona listas emergentes de finalizaciones posibles para los nombres de método, los elementos XML y otros elementos de codificación o marcado. En general, un gesto de usuario invoca una sesión de finalización. La sesión muestra la lista de finalizaciones posibles, y el usuario puede seleccionar uno o descartar la lista. El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> es responsable de crear y desencadenar el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcula el <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> de elementos de finalización de la sesión.

## <a name="see-also"></a>Vea también

- [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
- [Importaciones del Editor](../extensibility/editor-imports.md)