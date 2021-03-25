---
title: Dentro del editor
description: Obtenga información sobre los subsistemas y características del editor. Puede extender las características del editor de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bd45bb0a47de7283d75c083edc46b6fc38fe7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079207"
---
# <a name="inside-the-editor"></a>Dentro del editor

El editor se compone de varios subsistemas distintos, que están diseñados para mantener el modelo de texto del editor independiente de la vista de texto y la interfaz de usuario.

En estas secciones se describen distintos aspectos del editor:

- [Información general de los subsistemas](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [El modelo de texto](../extensibility/inside-the-editor.md#the-text-model)

- [La vista de texto](../extensibility/inside-the-editor.md#the-text-view)

En estas secciones se describen las características del editor:

- [Etiquetas y clasificadores](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Elementos gráficos](../extensibility/inside-the-editor.md#adornments)

- [Proyección](../extensibility/inside-the-editor.md#projection)

- [Esquematización](../extensibility/inside-the-editor.md#outlining)

- [Enlaces del mouse](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operaciones del editor](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Información general de los subsistemas

### <a name="text-model-subsystem"></a>Subsistema de modelo de texto

El subsistema del modelo de texto es responsable de representar el texto y habilitar su manipulación. El subsistema de modelo de texto contiene la <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz, que describe la secuencia de caracteres que va a mostrar el editor. Este texto se puede modificar, controlar y manipular de otra manera de muchas maneras. El modelo de texto también proporciona tipos para los siguientes aspectos:

- Un servicio que asocia texto a archivos y administra la lectura y escritura en el sistema de archivos.

- Un servicio de diferenciación que encuentra las diferencias mínimas entre dos secuencias de objetos.

- Sistema para describir el texto en un búfer en términos de subconjuntos del texto en otros búferes.

El subsistema del modelo de texto está libre de conceptos de la interfaz de usuario (UI). Por ejemplo, no es responsable del formato de texto ni del diseño de texto, y no tiene ningún conocimiento de los elementos visuales visuales que pueden estar asociados al texto.

Los tipos públicos del subsistema del modelo de texto están contenidos en *Microsoft.VisualStudio.Text.Data.dll* y *Microsoft.VisualStudio.CoreUtility.dll*, que solo dependen de la biblioteca de clases base .NET Framework y del Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Subsistema de vista de texto

El subsistema de vista de texto es responsable de dar formato al texto y mostrarlo. Los tipos de este subsistema se dividen en dos capas, en función de si los tipos se basan en Windows Presentation Foundation (WPF). Los tipos más importantes son <xref:Microsoft.VisualStudio.Text.Editor.ITextView> y <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , que controlan el conjunto de líneas de texto que se van a mostrar, así como el símbolo de intercalación, la selección y las funciones para adornar el texto mediante elementos de la interfaz de usuario de WPF. Este subsistema también proporciona márgenes alrededor del área de presentación del texto. Estos márgenes se pueden extender y pueden contener diferentes tipos de contenido y efectos visuales. Los ejemplos de márgenes son las pantallas de número de línea y las barras de desplazamiento.

Los tipos públicos del subsistema de vista de texto están contenidos en *Microsoft.VisualStudio.Text.UI.dll* y *Microsoft.VisualStudio.Text.UI.Wpf.dll*. El primer ensamblado contiene los elementos independientes de la plataforma y el segundo contiene los elementos específicos de WPF.

### <a name="classification-subsystem"></a>Subsistema de clasificación

El subsistema de clasificación es responsable de determinar las propiedades de fuente del texto. Un clasificador divide el texto en distintas clases, por ejemplo, "palabra clave" o "comentario". La asignación de formato de clasificación relaciona estas clases con las propiedades de fuente reales, por ejemplo, "consolas azules 10 pt". Esta información la usa la vista de texto cuando da formato y representa el texto. El etiquetado, que se describe con más detalle más adelante en este tema, permite asociar los datos con intervalos de texto.

Los tipos públicos del subsistema de clasificación están contenidos en Microsoft.VisualStudio.Text.Logic.dll e interactúan con los aspectos visuales de la clasificación, contenidos en Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Subsistema de operaciones

El subsistema de operaciones define el comportamiento del editor. Proporciona la implementación para los comandos del editor de Visual Studio y el sistema para deshacer.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Información más detallada sobre el modelo de texto y la vista de texto

### <a name="the-text-model"></a>El modelo de texto

El subsistema del modelo de texto consta de diferentes agrupaciones de tipos de texto. Entre ellos se incluyen el búfer de texto, las instantáneas de texto y los intervalos de texto.

#### <a name="text-buffers-and-text-snapshots"></a>Búferes de texto e instantáneas de texto

La <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaz representa una secuencia de caracteres Unicode que se codifican mediante UTF-16, que es la codificación utilizada por el `String` tipo en el .NET Framework. Un búfer de texto se puede almacenar como un documento de sistema de archivos, pero esto no es necesario.

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Se usa para crear un búfer de texto vacío o un búfer de texto que se inicializa a partir de una cadena o de <xref:System.IO.TextReader> . El búfer de texto se puede guardar en el sistema de archivos como <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Cualquier subproceso puede editar el búfer de texto hasta que un subproceso tome la propiedad del búfer de texto mediante una llamada a <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Después, solo ese subproceso puede realizar modificaciones.

Un búfer de texto puede pasar por varias versiones durante su duración. Se genera una nueva versión cada vez que se edita el búfer y un inmutable <xref:Microsoft.VisualStudio.Text.ITextSnapshot> representa el contenido de esa versión del búfer. Dado que las instantáneas de texto son inmutables, puede tener acceso a una instantánea de texto en cualquier subproceso, sin restricciones, aunque el búfer de texto que representa siga cambiando.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantáneas de texto y líneas de instantánea de texto

Puede ver el contenido de una instantánea de texto como una secuencia de caracteres o como una secuencia de líneas. Los caracteres y las líneas se indizan a partir de cero. Una instantánea de texto vacío contiene cero caracteres y una línea vacía. Una línea está delimitada por cualquier secuencia de caracteres Unicode de salto de línea válida, o por el principio o el final del búfer. Los caracteres de salto de línea se representan explícitamente en la instantánea de texto y los saltos de línea en una instantánea de texto no deben ser iguales.

> [!NOTE]
> Para obtener más información sobre los caracteres de salto de línea en el editor de Visual Studio, consulte [codificaciones y saltos de línea](../ide/encodings-and-line-breaks.md).

Una línea de texto se representa mediante un <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objeto, que se puede obtener a partir de una instantánea de texto para un número de línea determinado o para una posición de carácter determinada.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans y NormalizedSnapshotSpanCollections

<xref:Microsoft.VisualStudio.Text.SnapshotPoint>Representa una posición de carácter en una instantánea. Se garantiza que la posición se encuentra entre cero y la longitud de la instantánea. <xref:Microsoft.VisualStudio.Text.SnapshotSpan>Representa un intervalo de texto en una instantánea. Se garantiza que la posición final se encuentra entre cero y la longitud de la instantánea. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>Está compuesto por un conjunto de <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objetos de la misma instantánea.

#### <a name="spans-and-normalizedspancollections"></a>Intervalos y NormalizedSpanCollections

Un <xref:Microsoft.VisualStudio.Text.Span> representa un intervalo que se puede aplicar a un intervalo de texto en una instantánea de texto. Las posiciones de las instantáneas se basan en cero, por lo que los intervalos pueden comenzar en cualquier posición, lo que incluye cero. La `End` propiedad de un intervalo es igual a la suma de su `Start` propiedad y su `Length` propiedad. No `Span` incluye el carácter que la `End` propiedad indiza. Por ejemplo, un intervalo que tiene START = 5 y length = 3 tiene end = 8 e incluye los caracteres en las posiciones 5, 6 y 7. La notación de este intervalo es [5.. 8).

Dos intervalos forman una intersección si tienen posiciones en común, incluida la posición final. Por lo tanto, la intersección de [3, 5) y [2, 7) es [3, 5) y la intersección de [3, 5) y [5, 7) es [5, 5). (Observe que [5, 5) es un intervalo vacío).

Dos intervalos se superponen si tienen posiciones en común, salvo la posición final. Un intervalo vacío nunca se superpone a ningún otro intervalo y la superposición de dos intervalos nunca está vacía.

Una <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> es una lista de intervalos en el orden de las propiedades de inicio de los intervalos. En la lista, se combinan los intervalos coincidentes o contiguos. Por ejemplo, dado el conjunto de intervalos [5.. 9), [0.. 1), [3.. 6) y [9.. 10), la lista normalizada de intervalos es [0.. 1), [3.. 10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Notificaciones de cambio de ITextEdit, TextVersion y Text

El contenido de un búfer de texto se puede cambiar mediante un <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto. Al crear este tipo de objeto (mediante uno de los `CreateEdit()` métodos de <xref:Microsoft.VisualStudio.Text.ITextBuffer> ), se inicia una transacción de texto que se compone de ediciones de texto. Cada edición es un reemplazo de un intervalo de texto en el búfer por una cadena. Las coordenadas y el contenido de cada edición se expresan en relación con la instantánea del búfer al iniciarse la transacción. El <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto ajusta las coordenadas de las ediciones que se ven afectadas por otras ediciones de la misma transacción.

Por ejemplo, considere un búfer de texto que contiene esta cadena:

```
abcdefghij
```

Aplique una transacción que contenga dos ediciones, una edición que reemplace el intervalo en [2.. 4) mediante el carácter `X` y una segunda edición que reemplace el intervalo en [6.. 9] mediante el carácter `Y` . El resultado es este búfer:

```
abXefYj
```

Las coordenadas de la segunda edición se calcularon con respecto al contenido del búfer al principio de la transacción, antes de que se aplicara la primera edición.

Los cambios en el búfer surten efecto cuando <xref:Microsoft.VisualStudio.Text.ITextEdit> se confirma el objeto llamando a su `Apply()` método. Si había al menos una edición no vacía, se crea un nuevo <xref:Microsoft.VisualStudio.Text.ITextVersion> , se crea un nuevo <xref:Microsoft.VisualStudio.Text.ITextSnapshot> y `Changed` se genera un evento. Cada versión de texto tiene una instantánea de texto diferente. Una instantánea de texto representa el estado completo del búfer de texto después de una transacción de edición, pero una versión de texto solo describe los cambios de una instantánea a la siguiente. En general, las instantáneas de texto están diseñadas para usarse una vez y luego descartarse, mientras que las versiones de texto deben permanecer activas durante algún tiempo.

Una versión de texto contiene un <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Esta colección describe los cambios que, cuando se aplican a la instantánea, producen la instantánea siguiente. Cada <xref:Microsoft.VisualStudio.Text.ITextChange> de la colección contiene la posición de carácter del cambio, la cadena reemplazada y la cadena de reemplazo. La cadena reemplazada está vacía para una inserción básica y la cadena de reemplazo está vacía para una eliminación básica. La colección normalizada siempre es `null` para la versión más reciente del búfer de texto.

Solo <xref:Microsoft.VisualStudio.Text.ITextEdit> se puede crear una instancia de un objeto para un búfer de texto en cualquier momento y todas las ediciones de texto se deben realizar en el subproceso que posee el búfer de texto (si se ha reclamado la propiedad). Una edición de texto se puede abandonar llamando a su `Cancel` método o a su `Dispose` método.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> también proporciona `Insert()` `Delete()` `Replace()` los métodos, y que se parecen a los que se encuentran en la <xref:Microsoft.VisualStudio.Text.ITextEdit> interfaz. Llamar a estos tiene el mismo efecto que la creación de un <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto, la realización de una llamada similar y, a continuación, la aplicación de la edición.

#### <a name="tracking-points-and-tracking-spans"></a>Puntos de seguimiento y intervalos de seguimiento

<xref:Microsoft.VisualStudio.Text.ITrackingPoint>Representa una posición de carácter en un búfer de texto. Si el búfer se edita de manera que hace que la posición del carácter cambie, el punto de seguimiento se desplaza con él. Por ejemplo, si un punto de seguimiento hace referencia a la posición 10 de un búfer y se insertan cinco caracteres al principio del búfer, el punto de seguimiento hace referencia a la posición 15. Si se produce una inserción en la posición indicada por el punto de seguimiento, su comportamiento viene determinado por su <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , que puede ser `Positive` o `Negative` . Si el modo de seguimiento es positivo, el punto de seguimiento hace referencia al mismo carácter, que ahora se encuentra al final de la inserción. Si el modo de seguimiento es negativo, el punto de seguimiento hace referencia al primer carácter insertado en la posición original. Si se elimina el carácter situado en la posición representada por un punto de seguimiento, el punto de seguimiento se desplaza hasta el primer carácter que sigue al intervalo eliminado. Por ejemplo, si un punto de seguimiento hace referencia al carácter en la posición 5 y se eliminan los caracteres de las posiciones 3 a 6, el punto de seguimiento hace referencia al carácter que se encuentra en la posición 3.

<xref:Microsoft.VisualStudio.Text.ITrackingSpan>Representa un intervalo de caracteres en lugar de una sola posición. Su comportamiento viene determinado por su <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Si el modo de seguimiento del intervalo es [SpanTrackingMode. EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), el intervalo de seguimiento crece para incorporar el texto insertado en sus bordes. Si el modo de seguimiento del intervalo es [SpanTrackingMode. EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), el intervalo de seguimiento no incorpora el texto insertado en sus bordes. Sin embargo, si el modo de seguimiento del intervalo es [SpanTrackingMode. EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), una inserción inserta la posición actual hacia el inicio y, si el modo de seguimiento del intervalo es [SpanTrackingMode. EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), una inserción inserta la posición actual hacia el final.

Puede obtener la posición de un punto de seguimiento o el intervalo de un intervalo de seguimiento para cualquier instantánea del búfer de texto al que pertenecen. Se puede hacer referencia de forma segura a los puntos de seguimiento y los intervalos de seguimiento desde cualquier subproceso.

#### <a name="content-types"></a>Tipos de contenido

Los tipos de contenido son un mecanismo para definir diferentes tipos de contenido. Un tipo de contenido puede ser un tipo de archivo como "texto", "código" o "binario", o un tipo de tecnología como "XML", "VB" o "c#". Por ejemplo, la palabra "Using" es una palabra clave en C# y Visual Basic, pero no en otros lenguajes de programación. Por lo tanto, la definición de esta palabra clave se limitaría a los tipos de contenido "c#" y "VB".

Los tipos de contenido se utilizan como filtro para los elementos gráficos y otros elementos del editor. Muchas de las características del editor y los puntos de extensión se definen por tipo de contenido. Por ejemplo, el color del texto es diferente para los archivos de texto sin formato, los archivos XML y los archivos de código fuente de Visual Basic. Normalmente, los búferes de texto se asignan a un tipo de contenido cuando se crean y se puede cambiar el tipo de contenido de un búfer de texto.

Los tipos de contenido pueden heredar varios de otros tipos de contenido. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Permite especificar varios tipos base como los elementos primarios de un tipo de contenido determinado.

Los desarrolladores pueden definir sus propios tipos de contenido y registrarlos mediante el <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Muchas características del editor se pueden definir con respecto a un tipo de contenido específico mediante el <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Por ejemplo, los márgenes del editor, los elementos gráficos y los controladores de mouse se pueden definir para que se apliquen solo a los editores que muestran tipos de contenido concretos.

### <a name="the-text-view"></a>La vista de texto

La parte de la vista del modelo del controlador de vista de modelo (MVC) define la vista de texto, el formato de la vista, los elementos gráficos como la barra de desplazamiento y el símbolo de intercalación. Todos los elementos de presentación del editor de Visual Studio se basan en WPF.

#### <a name="text-views"></a>Vistas de texto

La <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interfaz es una representación independiente de la plataforma de una vista de texto. Se usa principalmente para mostrar documentos de texto en una ventana, pero también se puede usar para otros propósitos, por ejemplo, en una información sobre herramientas.

La vista de texto hace referencia a diferentes tipos de búferes de texto. La <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propiedad hace referencia a un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objeto que apunta a estos tres búferes de texto diferentes: el búfer de datos, que es el búfer de nivel de datos superior, el búfer de edición, en el que se produce la edición y el búfer visual, que es el búfer que se muestra en la vista de texto.

El formato del texto se basa en los clasificadores que están adjuntos al búfer de texto subyacente, y se adorna mediante los proveedores de elementos gráficos que están asociados a la propia vista de texto.

#### <a name="the-text-view-coordinate-system"></a>Sistema de coordenadas de la vista de texto

El sistema de coordenadas de la vista de texto especifica las posiciones en la vista de texto. En este sistema de coordenadas, el valor x 0,0 corresponde al borde izquierdo del texto que se muestra y el valor y 0,0 corresponde al borde superior del texto que se muestra. La coordenada x aumenta de izquierda a derecha y la coordenada y aumenta de arriba abajo.

Una ventanilla (la parte del texto visible en la ventana de texto) no se puede desplazar horizontalmente de la misma manera que se desplaza verticalmente. Una ventanilla se desplaza horizontalmente cambiando su coordenada izquierda para que se mueva con respecto a la superficie de dibujo. Sin embargo, una ventanilla solo se puede desplazar verticalmente cambiando el texto representado, lo que hace que <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> se genere un evento.

Las distancias en el sistema de coordenadas se corresponden con los píxeles lógicos. Si la superficie de representación de texto se muestra sin una transformación de escalado, una unidad en el sistema de coordenadas de representación de texto corresponde a un píxel de la pantalla.

#### <a name="margins"></a>Márgenes

La <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interfaz representa un margen y permite controlar la visibilidad del margen y su tamaño. Hay cuatro márgenes predefinidos, que se denominan "superior", "izquierda", "derecha" y "inferior" y se adjuntan al borde superior, inferior, izquierdo o derecho de una vista. Estos márgenes son contenedores en los que se pueden colocar otros márgenes. La interfaz define métodos que devuelven el tamaño del margen y la visibilidad de un margen. Los márgenes son elementos visuales que proporcionan información adicional sobre la vista de texto a la que están adjuntos. Por ejemplo, el margen línea-número muestra los números de línea de la vista de texto. El margen del glifo muestra los elementos de la interfaz de usuario.

La <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz controla la creación y la colocación de los márgenes. Los márgenes se pueden ordenar con respecto a otros márgenes. Los márgenes de prioridad más alta se encuentran más cerca de la vista de texto. Por ejemplo, si hay dos márgenes A la izquierda, el margen A y el margen B, y el margen B tiene una prioridad más baja que el margen a, el margen B aparece a la izquierda del margen A.

#### <a name="the-text-view-host"></a>El host de vista de texto

La <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interfaz contiene la vista de texto y cualquier decoración colindante que acompañe a la vista, por ejemplo, las barras de desplazamiento. El host de vista de texto también contiene márgenes asociados a un borde de la vista.

#### <a name="formatted-text"></a>Texto con formato

El texto que se muestra en una vista de texto se compone de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objetos. Cada línea de la vista de texto corresponde a una línea de texto en la vista de texto. Las líneas largas del búfer de texto subyacente pueden ocultarse parcialmente (si el ajuste de línea no está habilitado) o dividirse en varias líneas de la vista de texto. La <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interfaz contiene métodos y propiedades para la asignación entre coordenadas y caracteres, y para los elementos gráficos que se pueden asociar a la línea.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> los objetos se crean mediante una <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfaz. Si solo le preocupa el texto que se muestra actualmente en la vista, puede omitir el origen de formato. Si está interesado en el formato de texto que no se muestra en la vista (por ejemplo, para admitir un corte y pegado de texto enriquecido), puede usar <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> para dar formato al texto en un búfer de texto.

La vista de texto da formato a una sola <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> vez.

## <a name="editor-features"></a>Características del editor

Las características del editor están diseñadas para que la definición de la característica sea independiente de su implementación. El editor incluye estas características:

- Etiquetas y clasificadores

- Elementos gráficos

- Proyección

- esquematizar

- Enlaces de teclado y de mouse

- Operaciones y primitivas

- IntelliSense

### <a name="tags-and-classifiers"></a>Etiquetas y clasificadores

Las etiquetas son marcadores que están asociados a un intervalo de texto. Se pueden presentar de distintas maneras, por ejemplo, mediante el uso de colores de texto, subrayados, gráficos o elementos emergentes. Los clasificadores son un tipo de etiqueta.

Otros tipos de etiquetas son <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> para el resaltado de texto, la <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> esquematización y los <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> errores de compilación.

#### <a name="classification-types"></a>Tipos de clasificación

Una <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interfaz representa una clase de equivalencia, que es una categoría de texto abstracta. Los tipos de clasificación pueden heredar varios de otros tipos de clasificación. Por ejemplo, las clasificaciones del lenguaje de programación pueden incluir "palabra clave", "comentario" e "identificador", que heredan de "código". Los tipos de clasificación de lenguaje natural pueden incluir "Sustantivo", "Verb" y "adjetivo", que heredan de "natural Language".

#### <a name="classifications"></a>Clasificaciones

Una clasificación es una instancia de un tipo de clasificación determinado, normalmente en un intervalo de texto. <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>Se utiliza para representar una clasificación. Un intervalo de clasificación puede considerarse como una etiqueta que abarque un intervalo de texto determinado e indica al sistema que este intervalo de texto es de un tipo de clasificación determinado.

#### <a name="classifiers"></a>Clasificadores

Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> es un mecanismo que divide el texto en un conjunto de clasificaciones. Los clasificadores deben definirse para tipos de contenido específicos y se puede crear una instancia de ellos para búferes de texto específicos. Los clientes deben implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para participar en la clasificación de texto.

#### <a name="classifier-aggregators"></a>Agregadores clasificadores

Un agregador clasificador es un mecanismo que combina todos los clasificadores para un búfer de texto en un solo conjunto de clasificaciones. Por ejemplo, un clasificador de C# y un clasificador de idioma inglés pueden crear clasificaciones sobre un Comentario en un archivo de C#. Tenga en cuenta este comentario:

```
// This method produces a classifier
```

Un clasificador de C# podría etiquetar todo el intervalo como comentario y el clasificador del idioma inglés podría clasificar "genera" como "verbo" y "método" como "nombre". El agregador genera un conjunto de clasificaciones que no se superponen y el tipo del conjunto se basa en todas las contribuciones.

Un agregador clasificador también es un clasificador, ya que divide el texto en un conjunto de clasificaciones. El agregador clasificador también garantiza que no haya clasificaciones que se superpongan y que las clasificaciones se ordenen. Los clasificadores individuales pueden devolver cualquier conjunto de clasificaciones, en cualquier orden y superpuestas de cualquier manera.

#### <a name="classification-formatting-and-text-coloring"></a>Formato de clasificación y color del texto

El formato de texto es un ejemplo de una característica que se basa en la clasificación de texto. La capa de vista de texto la usa para determinar la presentación de texto en una aplicación. El área de formato del texto depende de WPF, pero no la definición lógica de las clasificaciones.

Un formato de clasificación es un conjunto de propiedades de formato para un tipo de clasificación específico. Estos formatos se heredan del formato del elemento primario del tipo de clasificación.

Una <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> es una asignación de un tipo de clasificación a un conjunto de propiedades de formato de texto. La implementación de la asignación de formato en el editor controla todas las exportaciones de formatos de clasificación.

### <a name="adornments"></a>Elementos gráficos

Los gráficos son efectos gráficos que no están directamente relacionados con la fuente y el color de los caracteres de la vista de texto. Por ejemplo, el subrayado ondulado de color rojo que se usa para marcar el código sin compilar en muchos lenguajes de programación es un elemento gráfico incrustado, y las informaciones sobre herramientas son elementos gráficos emergentes. Los elementos gráficos se derivan de <xref:System.Windows.UIElement> e implementan <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Dos tipos especializados de etiqueta de elemento gráfico son <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , para los elementos gráficos que ocupan el mismo espacio que el texto de una vista, y <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> para el subrayado en zigzag.

Los elementos gráficos incrustados son gráficos que forman parte de la vista de texto con formato. Se organizan en diferentes capas de orden Z. Hay tres capas integradas, como se indica a continuación: texto, el símbolo de intercalación y la selección. Sin embargo, los desarrolladores pueden definir más capas y colocarlas en orden con respecto a otras. Los tres tipos de elementos gráficos incrustados son elementos gráficos relativos a texto (que se mueven cuando se mueve el texto y se eliminan cuando se elimina el texto), los elementos gráficos relativos a las vistas (que tienen que ver con las partes que no son de texto de la vista) y los elementos gráficos controlados por el propietario (el desarrollador debe administrar su ubicación).

Los elementos gráficos emergentes son gráficos que aparecen en una ventana pequeña encima de la vista de texto, por ejemplo, información sobre herramientas.

### <a name="projection"></a><a name="projection"></a> Estando

La proyección es una técnica para construir un tipo diferente de búfer de texto que, en realidad, no almacena texto, sino que combina texto de otros búferes de texto. Por ejemplo, se puede utilizar un búfer de proyección para concatenar el texto de otros dos búferes y presentar el resultado como si estuviera en un solo búfer, o para ocultar partes del texto en un búfer. Un búfer de proyección puede actuar como un búfer de origen en otro búfer de proyección. Se puede construir un conjunto de búferes relacionados por proyección para reorganizar el texto de muchas maneras diferentes. (Este tipo de conjunto también se conoce como *gráfico de búfer*). La característica de esquematización de texto de Visual Studio se implementa mediante el uso de un búfer de proyección para ocultar el texto contraído y el editor de Visual Studio para páginas de ASP.NET utiliza la proyección para admitir lenguajes incrustados como Visual Basic y C#.

<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Se crea mediante <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Un búfer de proyección se representa mediante una secuencia ordenada de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objetos que se conocen como *intervalos de origen*. El contenido de estos intervalos se presenta como una secuencia de caracteres. Los búferes de texto desde los que se dibujan los intervalos de origen se denominan *búferes de origen*. Los clientes de un búfer de proyección no tienen que tener en cuenta que difiere de un búfer de texto ordinario.

El búfer de proyección escucha los eventos de cambio de texto en los búferes de origen. Cuando el texto de un intervalo de origen cambia, el búfer de proyección asigna las coordenadas de texto cambiadas a sus propias coordenadas y genera los eventos de cambio de texto adecuados. Por ejemplo, considere los búferes de origen A y B que tienen el siguiente contenido:

```
A: ABCDE
B: vwxyz
```

Si el búfer de proyección P se forma a partir de dos intervalos de texto, uno que tiene todo el búfer A y el otro con el búfer B, P tiene el siguiente contenido:

```
P: ABCDEvwxyz
```

Si la subcadena `xy` se elimina del búfer B, el búfer P genera un evento que indica que se eliminaron los caracteres de las posiciones 7 y 8.

El búfer de proyección también puede editarse directamente. Propaga las ediciones a los búferes de origen adecuados. Por ejemplo, si una cadena se inserta en el búfer P en la posición 6 (la posición original del carácter "v"), la inserción se propaga al búfer B en la posición 1.

Existen restricciones en los intervalos de origen que contribuyen a un búfer de proyección. Los intervalos de origen no pueden superponerse; una ubicación en un búfer de proyección no puede asignarse a más de una ubicación en ningún búfer de origen, y una ubicación en un búfer de origen no puede asignarse a más de una ubicación en un búfer de proyección. No se permiten circulares en la relación de búfer de origen.

Los eventos se generan cuando cambia el conjunto de búferes de origen para un búfer de proyección y cuando el conjunto de intervalos de origen cambia.
Un búfer de elisión es un tipo especial de búfer de proyección. Se utiliza principalmente para la esquematización y para las operaciones que expanden y contraen bloques de texto. Un búfer de elisión se basa en un solo búfer de origen y los intervalos en el búfer de elisión deben ordenarse de la misma forma en que se ordenan en el búfer de origen.

#### <a name="the-buffer-graph"></a>El gráfico de búfer

La <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interfaz permite la asignación a través de un gráfico de búferes de proyección. Todos los búferes de texto y los búferes de proyección se recopilan en un gráfico acíclicos dirigido, de forma muy similar al árbol de sintaxis abstracta que genera un compilador de lenguaje. El gráfico se define mediante el búfer superior, que puede ser cualquier búfer de texto. El gráfico de búfer puede asignar desde un punto del búfer superior hasta un punto en un búfer de origen o desde un intervalo del búfer superior hasta un conjunto de intervalos en un búfer de origen. Del mismo modo, puede asignar un punto o un intervalo desde un búfer de origen hasta un punto en el búfer superior. Los gráficos de búfer se crean mediante <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Eventos y búferes de proyección

Cuando se modifica un búfer de proyección, las modificaciones se envían desde el búfer de proyección a los búferes que dependen de ella. Una vez que se modifican todos los búferes, se generan eventos de cambio de búfer, comenzando por el búfer más profundo.

### <a name="outlining"></a>esquematizar

La esquematización es la capacidad de expandir o contraer diferentes bloques de texto en una vista de texto. La esquematización se define como un tipo de <xref:Microsoft.VisualStudio.Text.Tagging.ITag> , de la misma manera en que se definen los elementos gráficos. Una <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> es una etiqueta que define una región de texto que se puede expandir o contraer. Para usar la esquematización, debe importar <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> para obtener un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . El administrador de esquematización enumera, contrae y expande los distintos bloques, que se representan como <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objetos, y genera eventos en consecuencia.

### <a name="mouse-bindings"></a>Enlaces del mouse

Los enlaces del mouse vinculan los movimientos del mouse a distintos comandos. Los enlaces del mouse se definen mediante <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> , y los enlaces de teclado se definen mediante <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Crea automáticamente una instancia de todos los enlaces y los conecta a los eventos del mouse en la vista.

La <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interfaz contiene controladores de eventos anteriores y posteriores al procesamiento para los distintos eventos del mouse. Para controlar uno de los eventos, puede invalidar algunos de los métodos de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Operaciones del editor

Las operaciones del editor se pueden usar para automatizar la interacción con el editor, para el uso de scripts u otros fines. Puede importar el <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> para obtener acceso a las operaciones en un determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . A continuación, puede usar estos objetos para modificar la selección, desplazar la vista o desplazar el símbolo de intercalación a distintas partes de la vista.

### <a name="intellisense"></a>IntelliSense

IntelliSense admite la finalización de instrucciones, la ayuda para las firmas (también conocida como información de parámetros), la información rápida y las bombillas.

La finalización de instrucciones proporciona listas emergentes de posibles finalizaciones para los nombres de método, los elementos XML y otros elementos de código o de marcado. En general, un gesto de usuario invoca una sesión de finalización. La sesión muestra la lista de posibles finalizaciones y el usuario puede seleccionar una o descartar la lista. El <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> es responsable de crear y desencadenar el <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>Calcula el de los <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> elementos de finalización de la sesión.

## <a name="see-also"></a>Consulte también

- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
- [Importaciones del editor](../extensibility/editor-imports.md)
