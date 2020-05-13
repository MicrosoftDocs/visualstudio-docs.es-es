---
title: Dentro del editor
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710326"
---
# <a name="inside-the-editor"></a>Dentro del editor

El editor se compone de varios subsistemas diferentes, que están diseñados para mantener el modelo de texto del editor separado de la vista de texto y la interfaz de usuario.

Estas secciones describen diferentes aspectos del editor:

- [Resumen de los subsistemas](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [El modelo de texto](../extensibility/inside-the-editor.md#the-text-model)

- [La vista de texto](../extensibility/inside-the-editor.md#the-text-view)

Estas secciones describen las características del editor:

- [Etiquetas y clasificadores](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Adornos](../extensibility/inside-the-editor.md#adornments)

- [Proyección](../extensibility/inside-the-editor.md#projection)

- [esquematizar](../extensibility/inside-the-editor.md#outlining)

- [Fijaciones de ratón](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operaciones del editor](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Resumen de los subsistemas

### <a name="text-model-subsystem"></a>Subsistema de modelos de texto

El subsistema de modelo de texto es responsable de representar el texto y permitir su manipulación. El subsistema de <xref:Microsoft.VisualStudio.Text.ITextBuffer> modelo de texto contiene la interfaz, que describe la secuencia de caracteres que debe mostrar el editor. Este texto se puede modificar, rastrear y manipular de muchas maneras. El modelo de texto también proporciona tipos para los siguientes aspectos:

- Un servicio que asocia texto con archivos y administra la lectura y escritura en el sistema de archivos.

- Un servicio de diferenciación que encuentra las diferencias mínimas entre dos secuencias de objetos.

- Un sistema para describir el texto en un búfer en términos de subconjuntos del texto en otros búferes.

El subsistema de modelo de texto está libre de conceptos de interfaz de usuario (UI). Por ejemplo, no es responsable del formato del texto o del diseño del texto, y no tiene conocimiento de los adornos visuales que pueden estar asociados con el texto.

Los tipos públicos del subsistema de modelo de texto se encuentran en *Microsoft.VisualStudio.Text.Data.dll* y *Microsoft.VisualStudio.CoreUtility.dll*, que dependen únicamente de la biblioteca de clases base de .NET Framework y Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Subsistema de vista de texto

El subsistema de vista de texto es responsable de dar formato y mostrar texto. Los tipos de este subsistema se dividen en dos capas, dependiendo de si los tipos dependen de Windows Presentation Foundation (WPF). Los tipos más <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>importantes son y , que controlan el conjunto de líneas de texto que se van a mostrar, así como el intercalador, la selección y las facilidades para adornar el texto mediante elementos de interfaz de usuario de WPFWPF. Este subsistema también proporciona márgenes alrededor del área de visualización del texto. Estos márgenes se pueden ampliar y pueden contener diferentes tipos de contenido y efectos visuales. Ejemplos de márgenes son las visualizaciones de números de línea y las barras de desplazamiento.

Los tipos públicos del subsistema de vista de texto se encuentran en *Microsoft.VisualStudio.Text.UI.dll* y *Microsoft.VisualStudio.Text.UI.Wpf.dll*. El primer ensamblado contiene los elementos independientes de la plataforma y el segundo contiene los elementos específicos de WPFWPF.

### <a name="classification-subsystem"></a>Subsistema de clasificación

El subsistema de clasificación es responsable de determinar las propiedades de fuente para el texto. Un clasificador divide el texto en diferentes clases, por ejemplo, "palabra clave" o "comentario". El mapa de formato de clasificación relaciona estas clases con las propiedades de fuente reales, por ejemplo, "Blue Consolas 10 pt". Esta información la utiliza la vista de texto cuando da formato y representa texto. El etiquetado, que se describe con más detalle más adelante en este tema, permite que los datos se asocien con intervalos de texto.

Los tipos públicos del subsistema de clasificación están contenidos en Microsoft.VisualStudio.Text.Logic.dll y interactúan con los aspectos visuales de la clasificación, que se encuentran en Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Subsistema de operaciones

El subsistema de operaciones define el comportamiento del editor. Proporciona la implementación para los comandos del editor de Visual Studio y el sistema de deshacer.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Una mirada más cercana al modelo de texto y a la vista de texto

### <a name="the-text-model"></a>El modelo de texto

El subsistema de modelo de texto consta de diferentes agrupaciones de tipos de texto. Estos incluyen el búfer de texto, las instantáneas de texto y los intervalos de texto.

#### <a name="text-buffers-and-text-snapshots"></a>Búferes de texto e instantáneas de texto

La <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz representa una secuencia de caracteres Unicode que se codifican mediante `String` UTF-16, que es la codificación utilizada por el tipo en .NET Framework. Un búfer de texto se puede conservar como un documento del sistema de archivos, pero esto no es necesario.

Se <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> utiliza para crear un búfer de texto vacío o un búfer <xref:System.IO.TextReader>de texto que se inicializa desde una cadena o desde . El búfer de texto se puede conservar <xref:Microsoft.VisualStudio.Text.ITextDocument>en el sistema de archivos como un archivo .

Cualquier subproceso puede editar el búfer de texto hasta <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>que un subproceso tome la propiedad del búfer de texto llamando a . Después de eso, solo ese subproceso puede realizar ediciones.

Un búfer de texto puede pasar por muchas versiones durante su vida útil. Se genera una nueva versión cada vez que se <xref:Microsoft.VisualStudio.Text.ITextSnapshot> edita el búfer y un inmutable representa el contenido de esa versión del búfer. Dado que las instantáneas de texto son inmutables, puede tener acceso a una instantánea de texto en cualquier subproceso, sin restricciones, incluso si el búfer de texto que representa sigue cambiando.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantáneas de texto y líneas de instantáneas de texto

Puede ver el contenido de una instantánea de texto como una secuencia de caracteres o como una secuencia de líneas. Los caracteres y las líneas se indexan a partir de cero. Una instantánea de texto vacía contiene cero caracteres y una línea vacía. Una línea está delimitada por cualquier secuencia de caracteres de salto de línea Unicode válida o por el principio o el final del búfer. Los caracteres de salto de línea se representan explícitamente en la instantánea de texto y los saltos de línea de una instantánea de texto no tienen que ser todos iguales.

> [!NOTE]
> Para obtener más información acerca de los caracteres de salto de línea en el editor de Visual Studio, vea [codificaciones y saltos](../ide/encodings-and-line-breaks.md)de línea .

Una línea de texto se <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> representa mediante un objeto, que se puede obtener de una instantánea de texto para un número de línea determinado o para una posición de carácter determinada.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans y NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> representa una posición de carácter en una instantánea. Se garantiza que la posición se encuentra entre cero y la longitud de la instantánea. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> representa un intervalo de texto en una instantánea. Se garantiza que su posición final se encuentra entre cero y la longitud de la instantánea. Consta <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> de un <xref:Microsoft.VisualStudio.Text.SnapshotSpan> conjunto de objetos de la misma instantánea.

#### <a name="spans-and-normalizedspancollections"></a>Spans y NormalizedSpanCollections

A <xref:Microsoft.VisualStudio.Text.Span> representa un intervalo que se puede aplicar a un intervalo de texto en una instantánea de texto. Las posiciones de las instantáneas se basan en cero, por lo que los intervalos pueden comenzar en cualquier posición, incluido cero. La `End` propiedad de un intervalo es `Start` igual a `Length` la suma de su propiedad y su propiedad. A `Span` no incluye el carácter indizado por la `End` propiedad. Por ejemplo, un intervalo que tiene Start-5 y Length 3 tiene End-8, e incluye los caracteres en las posiciones 5, 6 y 7. La notación para este intervalo es [5..8).

Dos intervalos se intersecan si tienen alguna posición en común, incluida la posición Final. Por lo tanto, la intersección de [3, 5) y [2, 7) es [3, 5) y la intersección de [3, 5) y [5, 7) es [5, 5). (Tenga en cuenta que [5, 5) es un intervalo vacío.)

Dos intervalos se superponen si tienen posiciones en común, excepto la posición Final. Un intervalo vacío nunca se superpone a ningún otro intervalo y la superposición de dos intervalos nunca está vacía.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> es una lista de intervalos en el orden de las propiedades de inicio de los intervalos. En la lista, se combinan los intervalos superpuestos o colindantes. Por ejemplo, dado el conjunto de intervalos [5..9), [0..1), [3..6) y [9..10), la lista normalizada de intervalos es [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion y notificaciones de cambio de texto

El contenido de un búfer de <xref:Microsoft.VisualStudio.Text.ITextEdit> texto se puede cambiar mediante un objeto. La creación de un objeto `CreateEdit()` de <xref:Microsoft.VisualStudio.Text.ITextBuffer>este tipo (mediante uno de los métodos de ) inicia una transacción de texto que consta de ediciones de texto. Cada edición es un reemplazo de algún intervalo de texto en el búfer por una cadena. Las coordenadas y el contenido de cada edición se expresan en relación con la instantánea del búfer cuando se inició la transacción. El <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto ajusta las coordenadas de las ediciones que se ven afectadas por otras ediciones en la misma transacción.

Por ejemplo, considere un búfer de texto que contenga esta cadena:

```
abcdefghij
```

Aplique una transacción que contenga dos ediciones, una edición que reemplace el `X` intervalo en [2..4) utilizando el carácter y `Y`una segunda edición que reemplace el intervalo en [6..9) utilizando el carácter . El resultado es este buffer:

```
abXefYj
```

Las coordenadas de la segunda edición se calcularon con respecto al contenido del búfer al principio de la transacción, antes de aplicar la primera edición.

Los cambios en el <xref:Microsoft.VisualStudio.Text.ITextEdit> búfer surten `Apply()` efecto cuando se confirma el objeto llamando a su método. Si hubo al menos una edición <xref:Microsoft.VisualStudio.Text.ITextVersion> no vacía, <xref:Microsoft.VisualStudio.Text.ITextSnapshot> se crea una `Changed` nueva, se crea una nueva y se genera un evento. Cada versión de texto tiene una instantánea de texto diferente. Una instantánea de texto representa el estado completo del búfer de texto después de una transacción de edición, pero una versión de texto describe solo los cambios de una instantánea a la siguiente. En general, las instantáneas de texto están diseñadas para usarse una vez y, a continuación, se descartan, mientras que las versiones de texto deben permanecer vivas durante algún tiempo.

Una versión <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>de texto contiene un archivo . Esta colección describe los cambios que, cuando se aplican a la instantánea, producen la instantánea posterior. Cada <xref:Microsoft.VisualStudio.Text.ITextChange> parte de la colección contiene la posición del carácter del cambio, la cadena reemplazada y la cadena de reemplazo. La cadena reemplazada está vacía para una inserción básica y la cadena de reemplazo está vacía para una eliminación básica. La colección normalizada siempre `null` es para la versión más reciente del búfer de texto.

Solo <xref:Microsoft.VisualStudio.Text.ITextEdit> se puede crear una instancia de un objeto para un búfer de texto en cualquier momento y todas las ediciones de texto se deben realizar en el subproceso que posee el búfer de texto (si se ha reclamado la propiedad). Una edición de texto `Cancel` se puede `Dispose` abandonar llamando a su método o a su método.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>también `Insert()`proporciona `Delete()`, `Replace()` , y métodos <xref:Microsoft.VisualStudio.Text.ITextEdit> que se asemejan a los que se encuentran en la interfaz. Llamar a estos tiene el <xref:Microsoft.VisualStudio.Text.ITextEdit> mismo efecto que crear un objeto, realizar la llamada similar y, a continuación, aplicar la edición.

#### <a name="tracking-points-and-tracking-spans"></a>Puntos de seguimiento y intervalos de seguimiento

Un <xref:Microsoft.VisualStudio.Text.ITrackingPoint> representa una posición de carácter en un búfer de texto. Si el búfer se edita de una manera que hace que la posición del carácter cambie, el punto de seguimiento cambia con él. Por ejemplo, si un punto de seguimiento hace referencia a la posición 10 en un búfer y se insertan cinco caracteres al principio del búfer, el punto de seguimiento hace referencia a la posición 15. Si una inserción se produce precisamente en la posición <xref:Microsoft.VisualStudio.Text.PointTrackingMode>indicada por el `Positive` `Negative`punto de seguimiento, su comportamiento viene determinado por su , que puede ser o . Si el modo de seguimiento es positivo, el punto de seguimiento hace referencia al mismo carácter, que ahora está al final de la inserción. Si el modo de seguimiento es negativo, el punto de seguimiento hace referencia al primer carácter insertado en la posición original. Si se elimina el carácter en la posición representada por un punto de seguimiento, el punto de seguimiento cambia al primer carácter que sigue al intervalo eliminado. Por ejemplo, si un punto de seguimiento hace referencia al carácter en la posición 5 y se eliminan los caracteres de las posiciones 3 a 6, el punto de seguimiento hace referencia al carácter en la posición 3.

Un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representa un rango de caracteres en lugar de una sola posición. Su comportamiento está <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>determinado por su . Si el modo de seguimiento de intervalo es [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), el intervalo de seguimiento crece para incorporar texto insertado en sus bordes. Si el modo de seguimiento de intervalo es [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), el intervalo de seguimiento no incorpora texto insertado en sus bordes. Sin embargo, si el modo de seguimiento de intervalo es [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), una inserción inserta la posición actual hacia el inicio y si el modo de seguimiento de intervalo es [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), una inserción empuja la posición actual hacia el final.

Puede obtener la posición de un punto de seguimiento o el intervalo de un intervalo de seguimiento para cualquier instantánea del búfer de texto al que pertenecen. Los puntos de seguimiento y los intervalos de seguimiento se pueden hacer referencia de forma segura desde cualquier subproceso.

#### <a name="content-types"></a>Tipos de contenido

Los tipos de contenido son un mecanismo para definir diferentes tipos de contenido. Un tipo de contenido puede ser un tipo de archivo como "text", "code" o "binary", o un tipo de tecnología como "xml", "vb" o "c-". Por ejemplo, la palabra "usar" es una palabra clave tanto en C- como en Visual Basic, pero no en otros lenguajes de programación. Por lo tanto, la definición de esta palabra clave se limitaría a los tipos de contenido "c" y "vb".

Los tipos de contenido se utilizan como filtro para adornos y otros elementos del editor. Muchas características del editor y puntos de extensión se definen por tipo de contenido. Por ejemplo, el color de texto es diferente para los archivos de texto sin formato, los archivos XML y los archivos de código fuente de Visual Basic. Los búferes de texto generalmente se asignan un tipo de contenido cuando se crean y el tipo de contenido de un búfer de texto se puede cambiar.

Los tipos de contenido pueden heredar varios de otros tipos de contenido. Le <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> permite especificar varios tipos base como los elementos primarios de un tipo de contenido determinado.

Los desarrolladores pueden definir sus propios <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>tipos de contenido y registrarlos mediante el archivo . Muchas características del editor se pueden definir con <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>respecto a un tipo de contenido específico mediante el uso de la . Por ejemplo, los márgenes del editor, los adornos y los controladores del mouse se pueden definir para que se apliquen solo a los editores que muestran determinados tipos de contenido.

### <a name="the-text-view"></a>La vista de texto

La parte de vista del patrón de controlador de vista de modelo (MVC) define la vista de texto, el formato de la vista, los elementos gráficos como la barra de desplazamiento y el icono de intercalación. Todos los elementos de presentación del editor de Visual Studio se basan en WPFWPF.

#### <a name="text-views"></a>Vistas de texto

La <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaz es una representación independiente de la plataforma de una vista de texto. Se utiliza principalmente para mostrar documentos de texto en una ventana, pero también se puede utilizar para otros fines, por ejemplo, en una información sobre herramientas.

La vista de texto hace referencia a diferentes tipos de búferes de texto. La <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propiedad hace <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> referencia a un objeto que apunta a estos tres búferes de texto diferentes: el búfer de datos, que es el búfer de nivel de datos superior, el búfer de edición, en el que se produce la edición, y el búfer visual, que es el búfer que se muestra en la vista de texto.

El texto se formatea en función de los clasificadores que se adjuntan al búfer de texto subyacente y se adorna mediante los proveedores de adornos que se adjuntan a la propia vista de texto.

#### <a name="the-text-view-coordinate-system"></a>El sistema de coordenadas de vista de texto

El sistema de coordenadas de vista de texto especifica posiciones en la vista de texto. En este sistema de coordenadas, el valor x 0.0 corresponde al borde izquierdo del texto que se muestra y el valor y 0.0 corresponde al borde superior del texto que se muestra. La coordenada x aumenta de izquierda a derecha, y la coordenada y aumenta de arriba a abajo.

Una ventana gráfica (la parte del texto visible en la ventana de texto) no se puede desplazar de la misma manera que se desplaza verticalmente. Una ventana gráfica se desplaza horizontalmente cambiando su coordenada izquierda para que se mueva con respecto a la superficie de dibujo. Sin embargo, una ventana gráfica solo se puede desplazar verticalmente cambiando el texto representado, lo que hace que se genere un <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.

Las distancias en el sistema de coordenadas corresponden a píxeles lógicos. Si la superficie de representación de texto se muestra sin una transformación de escala, una unidad del sistema de coordenadas de representación de texto corresponde a un píxel de la pantalla.

#### <a name="margins"></a>Márgenes

La <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaz representa un margen y permite controlar la visibilidad del margen y su tamaño. Hay cuatro márgenes predefinidos, que se denominan "Arriba", "Izquierda", "Derecha" y "Inferior" y están unidos al borde superior, inferior, izquierdo o derecho de una vista. Estos márgenes son contenedores en los que se pueden colocar otros márgenes. La interfaz define métodos que devuelven el tamaño del margen y la visibilidad de un margen. Los márgenes son elementos visuales que proporcionan información adicional sobre la vista de texto a la que están asociados. Por ejemplo, el margen de número de línea muestra números de línea para la vista de texto. El margen de glifo muestra elementos de interfaz de usuario.

La <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz controla la creación y colocación de márgenes. Los márgenes se pueden ordenar con respecto a otros márgenes. Los márgenes de mayor prioridad se encuentran más cerca de la vista de texto. Por ejemplo, si hay dos márgenes izquierdos, el margen A y el margen B, y el margen B tiene una prioridad menor que el margen A, el margen B aparece a la izquierda del margen A.

#### <a name="the-text-view-host"></a>El host de vista de texto

La <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaz contiene la vista de texto y las decoraciones colindantes que acompañan a la vista, por ejemplo, las barras de desplazamiento. El host de vista de texto también contiene márgenes que se adjuntan a un borde de la vista.

#### <a name="formatted-text"></a>Texto con formato

El texto que se muestra en una <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> vista de texto se compone de objetos. Cada línea de vista de texto corresponde a una línea de texto en la vista de texto. Las líneas largas en el búfer de texto subyacente pueden oscurecerse parcialmente (si el ajuste de palabras no está habilitado) o dividirse en varias líneas de vista de texto. La <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaz contiene métodos y propiedades para la asignación entre coordenadas y caracteres, y para los adornos que pueden estar asociados a la línea.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>los objetos se <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> crean mediante una interfaz. Si solo le preocupa el texto que se muestra actualmente en la vista, puede omitir el origen de formato. Si está interesado en el formato de texto que no se muestra en la vista (por ejemplo, para admitir un corte y pegado de texto enriquecido), puede usarlo para dar <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> formato al texto en un búfer de texto.

La vista de <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> texto da formato de uno en uno.

## <a name="editor-features"></a>Características del editor

Las características del editor están diseñadas para que la definición de la característica sea independiente de su implementación. El editor incluye estas características:

- Etiquetas y clasificadores

- Adornos

- Proyección

- esquematizar

- Enlaces de ratón y teclas

- Operaciones y primitivos

- IntelliSense

### <a name="tags-and-classifiers"></a>Etiquetas y clasificadores

Las etiquetas son marcadores asociados a un intervalo de texto. Se pueden presentar de diferentes maneras, por ejemplo, mediante el uso de coloración de texto, subrayados, gráficos o ventanas emergentes. Los clasificadores son un tipo de etiqueta.

Otros tipos de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> etiquetas son <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> para resaltar texto, para esquematización y <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> para errores de compilación.

#### <a name="classification-types"></a>Tipos de clasificación

Una <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaz representa una clase de equivalencia, que es una categoría abstracta de texto. Los tipos de clasificación pueden heredar varios de otros tipos de clasificación. Por ejemplo, las clasificaciones de lenguaje de programación pueden incluir "palabra clave", "comentario" e "identificador", que heredan de "código". Los tipos de clasificación de lenguaje natural pueden incluir "nombre", "verbo" y "adjetivo", que heredan del "lenguaje natural".

#### <a name="classifications"></a>Classifications

Una clasificación es una instancia de un tipo de clasificación determinado, normalmente en un intervalo de texto. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> se utiliza para representar una clasificación. Un intervalo de clasificación se puede considerar como una etiqueta que cubre un intervalo de texto determinado y le dice al sistema que este intervalo de texto es de un tipo de clasificación determinado.

#### <a name="classifiers"></a>Clasificadores

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> es un mecanismo que divide el texto en un conjunto de clasificaciones. Los clasificadores deben definirse para tipos de contenido específicos y crear instancias para búferes de texto específicos. Los clientes deben implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para participar en la clasificación de texto.

#### <a name="classifier-aggregators"></a>Agregadores clasificadores

Un agregador de clasificador es un mecanismo que combina todos los clasificadores para un búfer de texto en un solo conjunto de clasificaciones. Por ejemplo, tanto un clasificador de C- como un clasificador de idioma inglés podrían crear clasificaciones sobre un comentario en un archivo de C. Considere este comentario:

```
// This method produces a classifier
```

Un clasificador de C- podría etiquetar todo el intervalo como un comentario, y el clasificador de idioma inglés podría clasificar "produce" como un "verbo" y "método" como un "nombre". El agregador produce un conjunto de clasificaciones no superpuestas y el tipo del conjunto se basa en todas las contribuciones.

Un agregador clasificador también es un clasificador porque divide el texto en un conjunto de clasificaciones. El agregador clasificador también garantiza que no haya clasificaciones superpuestas y que las clasificaciones estén ordenadas. Los clasificadores individuales son libres de devolver cualquier conjunto de clasificaciones, en cualquier orden, y superponerse de cualquier manera.

#### <a name="classification-formatting-and-text-coloring"></a>Formato de clasificación y coloración del texto

El formato de texto es un ejemplo de una característica que se basa en la clasificación de texto. La capa de vista de texto lo utiliza para determinar la visualización del texto en una aplicación. El área de formato de texto depende de WPFWPF, pero la definición lógica de clasificaciones no lo hace.

Un formato de clasificación es un conjunto de propiedades de formato para un tipo de clasificación específico. Estos formatos heredan del formato del elemento primario del tipo de clasificación.

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> es un mapa de un tipo de clasificación a un conjunto de propiedades de formato de texto. La implementación del mapa de formato en el editor controla todas las exportaciones de formatos de clasificación.

### <a name="adornments"></a>Adornos

Los adornos son efectos gráficos que no están directamente relacionados con la fuente y el color de los caracteres de la vista de texto. Por ejemplo, el subrayado de ondulación roja que se utiliza para marcar código no compilar en muchos lenguajes de programación es un adorno incrustado y las descripciones emergentes son adornos emergentes. Los adornos se <xref:System.Windows.UIElement> derivan <xref:Microsoft.VisualStudio.Text.Tagging.ITag>e implementan. Dos tipos especializados de etiqueta <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>de adorno son el , para los adornos <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>que ocupan el mismo espacio que el texto en una vista, y el , para el subrayado ondulado.

Los adornos incrustados son gráficos que forman parte de la vista de texto con formato. Se organizan en diferentes capas de orden Z. Hay tres capas integradas, como se indica a continuación: texto, el intercalador y la selección. Sin embargo, los desarrolladores pueden definir más capas y ponerlas en orden con respecto a la otra. Los tres tipos de adornos incrustados son adornos relativos al texto (que se mueven cuando se mueve el texto y se eliminan cuando se elimina el texto), adornos relativos a la vista (que tienen que ver con partes que no son de texto de la vista) y adornos controlados por el propietario (el desarrollador debe administrar su ubicación).

Los adornos emergentes son gráficos que aparecen en una pequeña ventana sobre la vista de texto, por ejemplo, información sobre herramientas.

### <a name="projection"></a><a name="projection"></a>Proyección

La proyección es una técnica para construir un tipo diferente de búfer de texto que en realidad no almacena texto, sino que combina texto de otros búferes de texto. Por ejemplo, un búfer de proyección se puede utilizar para concatenar el texto de otros dos búferes y presentar el resultado como si estuviera en un solo búfer, o para ocultar partes del texto en un búfer. Un búfer de proyección puede actuar como búfer de origen en otro búfer de proyección. Se puede construir un conjunto de búferes relacionados por proyección para reorganizar el texto de muchas maneras diferentes. (Este conjunto también se conoce como *gráfico de búfer*.) La característica de esquematización de texto de Visual Studio se implementa mediante un búfer de proyección para ocultar el texto contraído y el editor de Visual Studio para ASP.NET páginas usa la proyección para admitir lenguajes incrustados como Visual Basic y C.

Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> se crea <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>mediante . Un búfer de proyección se <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representa mediante una secuencia ordenada de objetos que se conocen como intervalos de *origen.* El contenido de estos intervalos se presenta como una secuencia de caracteres. Los búferes de texto desde los que se extraen los intervalos de origen se denominan búferes de *origen.* Los clientes de un búfer de proyección no tienen que ser conscientes de que difiere de un búfer de texto normal.

El búfer de proyección escucha eventos de cambio de texto en los búferes de origen. Cuando cambia el texto de un intervalo de origen, el búfer de proyección asigna las coordenadas de texto modificadas a sus propias coordenadas y genera los eventos de cambio de texto adecuados. Por ejemplo, considere los búferes de origen A y B que tienen estos contenidos:

```
A: ABCDE
B: vwxyz
```

Si el búfer de proyección P se forma a partir de dos intervalos de texto, uno que tiene todo el búfer A y el otro que tiene todo el búfer B, Entonces P tiene el siguiente contenido:

```
P: ABCDEvwxyz
```

Si la `xy` subcadena se elimina del búfer B, el búfer P genera un evento que indica que se eliminaron los caracteres de las posiciones 7 y 8.

El búfer de proyección también se puede editar directamente. Propaga las ediciones a los búferes de origen adecuados. Por ejemplo, si se inserta una cadena en el búfer P en la posición 6 (la posición original del carácter "v"), la inserción se propaga al búfer B en la posición 1.

Hay restricciones en los intervalos de origen que contribuyen a un búfer de proyección. Los intervalos de origen no pueden superponerse; una ubicación en un búfer de proyección no se puede asignar a más de una ubicación en cualquier búfer de origen y una ubicación en un búfer de origen no se puede asignar a más de una ubicación en un búfer de proyección. No se permiten circularidades en la relación de búfer de origen.

Los eventos se generan cuando cambia el conjunto de búferes de origen para un búfer de proyección y cuando cambia el conjunto de intervalos de origen.
Un búfer de elision es un tipo especial de búfer de proyección. Se utiliza principalmente para esquematización y para operaciones que expanden y contraen bloques de texto. Un búfer de elision se basa en un solo búfer de origen y los intervalos en el búfer de elision se deben ordenar de la misma manera que se ordenan en el búfer de origen.

#### <a name="the-buffer-graph"></a>El gráfico de búfer

La <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaz permite la asignación a través de un gráfico de búferes de proyección. Todos los búferes de texto y los búferes de proyección se recopilan en un gráfico acíclico dirigido, al igual que el árbol de sintaxis abstracta generado por un compilador de lenguaje. El gráfico se define mediante el búfer superior, que puede ser cualquier búfer de texto. El gráfico de búfer puede asignar desde un punto del búfer superior a un punto de un búfer de origen o de un intervalo en el búfer superior a un conjunto de intervalos en un búfer de origen. De forma similar, puede asignar un punto o un intervalo de un búfer de origen a un punto del búfer superior. Los gráficos de búfer <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>se crean mediante el archivo .

#### <a name="events-and-projection-buffers"></a>Eventos y búferes de proyección

Cuando se modifica un búfer de proyección, las modificaciones se envían desde el búfer de proyección a los búferes que dependen de él. Después de modificar todos los búferes, se generan eventos de cambio de búfer, empezando por el búfer más profundo.

### <a name="outlining"></a>esquematizar

Esquema es la capacidad de expandir o contraer diferentes bloques de texto en una vista de texto. La esquematización se <xref:Microsoft.VisualStudio.Text.Tagging.ITag>define como una especie de , de la misma manera que se definen los adornos. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> es una etiqueta que define una región de texto que se puede expandir o contraer. Para usar la esquematización, debe importar el <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> para obtener un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>archivo . El administrador de esquematización enumera, contrae y expande los <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> diferentes bloques, que se representan como objetos, y genera eventos en consecuencia.

### <a name="mouse-bindings"></a>Fijaciones de ratón

Los enlaces de ratón vinculan los movimientos del ratón a diferentes comandos. Los enlaces de mouse <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>se definen mediante un <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>archivo , y los enlaces de clave se definen mediante un archivo . La <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> instancia automática de todos los enlaces y los conecta a eventos del mouse en la vista.

La <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaz contiene controladores de eventos previos y posteriores al proceso para diferentes eventos del mouse. Para controlar uno de los eventos, puede <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>invalidar algunos de los métodos de .

### <a name="editor-operations"></a>Operaciones del editor

Las operaciones del editor se pueden utilizar para automatizar la interacción con el editor, con fines de scripting u otros fines. Puede importar <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> las operaciones de <xref:Microsoft.VisualStudio.Text.Editor.ITextView>acceso a un archivo . A continuación, puede utilizar estos objetos para modificar la selección, desplazar la vista o mover el símbolo de intercalación a diferentes partes de la vista.

### <a name="intellisense"></a>IntelliSense

IntelliSense admite la finalización de instrucciones, la ayuda de firma (también conocida como información de parámetros), información rápida y bombillas.

La finalización de instrucciones proporciona listas emergentes de posibles terminaciones para nombres de método, elementos XML y otros elementos de codificación o marcado. En general, un gesto de usuario invoca una sesión de finalización. La sesión muestra la lista de posibles terminaciones y el usuario puede seleccionar una o descartar la lista. El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> es responsable de crear <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>y desencadenar el archivo . El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> proceso <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> calcula los elementos de finalización de la sesión.

## <a name="see-also"></a>Vea también

- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
- [Importaciones de editores](../extensibility/editor-imports.md)
