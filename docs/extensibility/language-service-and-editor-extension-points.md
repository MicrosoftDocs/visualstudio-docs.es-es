---
title: Puntos de extensión de editor y servicio de lenguaje | Microsoft Docs
description: Obtenga información sobre los puntos de extensión en el editor de código de Visual Studio que puede extender, incluidas la mayoría de las características del servicio de lenguaje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a8d71e6c7cd7569c9e73134345584a8237337bc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073305"
---
# <a name="language-service-and-editor-extension-points"></a>Puntos de extensión de editor y servicio de lenguaje
El editor de proporciona puntos de extensión que se pueden extender como partes de componentes de Managed Extensibility Framework (MEF), incluidas la mayoría de las características del servicio de lenguaje. Estas son las categorías principales de puntos de extensión:

- Tipos de contenido

- Tipos de clasificación y formatos de clasificación

- Márgenes y barras de desplazamiento

- Etiquetas

- Elementos gráficos

- Procesadores de mouse

- Quitar controladores

- Opciones

- IntelliSense

## <a name="extend-content-types"></a>Extender tipos de contenido
 Los tipos de contenido son las definiciones de los tipos de texto administrados por el editor, por ejemplo, "Text", "Code" o "CSharp". Para definir un nuevo tipo de contenido, debe declarar una variable del tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> y asignar un nombre único al nuevo tipo de contenido. Para registrar el tipo de contenido con el editor, expórtelo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> es el nombre del tipo de contenido.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> es el nombre del tipo de contenido del que se deriva este tipo de contenido. Un tipo de contenido puede heredar de varios otros tipos de contenido.

  Dado <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> que la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de tipo de contenido.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Los tipos de contenido se pueden basar en cero o más tipos de contenido ya existentes. Estos son los tipos integrados:

- Any: el tipo de contenido Basic. Elemento primario de todos los demás tipos de contenido.

- Text: el tipo básico para el contenido que no es de proyección. Hereda de "any".

- Texto no cifrado: para texto sin código. Hereda de "Text".

- Código: para el código de todos los tipos. Hereda de "Text".

- Inerte: excluye el texto de cualquier tipo de control. El texto de este tipo de contenido nunca tendrá ninguna extensión aplicada.

- Proyección: para el contenido de los búferes de proyección. Hereda de "any".

- IntelliSense: para el contenido de IntelliSense. Hereda de "Text".

- Sighelp: ayuda para las firmas. Hereda de "IntelliSense".

- Sighelp-doc: documentación de ayuda para las firmas. Hereda de "IntelliSense".

  Estos son algunos de los tipos de contenido definidos por Visual Studio y algunos de los lenguajes que se hospedan en Visual Studio:

- Básico

- C/C++

- ConsoleOutput

- CSharp

- CSS

- ENC

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Para detectar la lista de tipos de contenido disponibles, importe el <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , que mantiene la colección de tipos de contenido para el editor. En el código siguiente se importa este servicio como una propiedad.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Para asociar un tipo de contenido a una extensión de nombre de archivo, use <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> En Visual Studio, las extensiones de nombre de archivo se registran mediante el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> en un paquete del servicio de lenguaje. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>Asocia un tipo de contenido de MEF con una extensión de nombre de archivo que se ha registrado de esta manera.

 Para exportar la extensión de nombre de archivo a la definición de tipo de contenido, debe incluir los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: especifica la extensión de nombre de archivo.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: especifica el tipo de contenido.

  Dado <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación de una extensión de nombre de archivo en una definición de tipo de contenido.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>Administra las asociaciones entre las extensiones de nombre de archivo y los tipos de contenido.

## <a name="extend-classification-types-and-classification-formats"></a>Extender tipos de clasificación y formatos de clasificación
 Puede usar tipos de clasificación para definir los tipos de texto para los que desea proporcionar un control diferente (por ejemplo, colorear el texto "palabra clave" azul y el texto "comentario" en verde). Defina un nuevo tipo de clasificación declarando una variable de tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> y asignándole un nombre único.

 Para registrar el tipo de clasificación con el editor, expórtelo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del tipo de clasificación.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: el nombre del tipo de clasificación del que se hereda este tipo de clasificación. Todos los tipos de clasificación heredan de "Text", y un tipo de clasificación puede heredar de varios otros tipos de clasificación.

  Dado <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> que la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de tipo de clasificación.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 El <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> proporciona acceso a las clasificaciones estándar. Entre los tipos de clasificación integrados se incluyen los siguientes:

- "text"

- "lenguaje natural" (se deriva de "Text")

- "lenguaje formal" (se deriva de "Text")

- "cadena" (se deriva de "literal")

- "carácter" (se deriva de "literal")

- "numérico" (se deriva de "literal")

  Un conjunto de distintos tipos de error heredan de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Incluyen los siguientes tipos de error:

- "error de sintaxis"

- "error del compilador"

- "otro error"

- atención

  Para detectar la lista de tipos de clasificación disponibles, importe el <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , que mantiene la colección de tipos de clasificación para el editor. En el código siguiente se importa este servicio como una propiedad.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Puede definir una definición de formato de clasificación para el nuevo tipo de clasificación. Derive una clase de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> y expórtela con el tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> , junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: el nombre para mostrar del formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: especifica si el formato aparece en la página **fuentes y colores** del cuadro de diálogo **Opciones** .

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la prioridad del formato. Los valores válidos son de <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: el nombre del tipo de clasificación al que está asignado este formato.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de formato de clasificación.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Para detectar la lista de formatos disponibles, importe el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , que mantiene la colección de formatos para el editor. En el código siguiente se importa este servicio como una propiedad.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Extender los márgenes y las barras de desplazamiento
 Los márgenes y las barras de desplazamiento son los elementos de la vista principal del editor, además de la propia vista de texto. Puede proporcionar cualquier número de márgenes, además de los márgenes estándar que aparecen alrededor de la vista de texto.

 Implemente una <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfaz para definir un margen. También debe implementar la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz para crear el margen.

 Para registrar el proveedor de margen con el editor, debe exportar el proveedor junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del margen.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que aparece el margen, en relación con los demás márgenes.

   Estos son los márgenes integrados:

  - "Barra de desplazamiento horizontal de WPF"

  - "Barra de desplazamiento vertical de WPF"

  - "Margen de número de línea de WPF"

    Los márgenes horizontales que tienen un atributo de orden de `After="Wpf Horizontal Scrollbar"` se muestran debajo del margen integrado, y los márgenes horizontales que tienen un atributo de orden de `Before ="Wpf Horizontal Scrollbar"` se muestran por encima del margen integrado. Los márgenes verticales a la derecha que tienen el atributo order de `After="Wpf Vertical Scrollbar"` se muestran a la derecha de la barra de desplazamiento. Los márgenes verticales izquierdos que tienen un atributo de orden `After="Wpf Line Number Margin"` aparecen a la izquierda del margen del número de línea (si es visible).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: el tipo de margen (izquierda, derecha, superior o inferior).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que el margen es válido.

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de margen para un margen que aparece a la derecha del margen del número de línea.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Extender etiquetas
 Las etiquetas son una manera de asociar los datos con distintos tipos de texto. En muchos casos, los datos asociados se muestran como un efecto visual, pero no todas las etiquetas tienen una presentación visual. Puede definir su propio tipo de etiqueta implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . También debe implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> para proporcionar las etiquetas para un conjunto determinado de intervalos de texto y <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> para proporcionar el etiquetador. Debe exportar el proveedor de etiquetadores junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que la etiqueta es válida.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta.

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de etiquetadores.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> los siguientes tipos de etiqueta están integrados:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: asociado a <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: asociado a tipos de error.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: está asociado a un elemento gráfico.

  > [!NOTE]
  > Para obtener un ejemplo de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , vea la definición de HighlightWordTag en [Tutorial: resaltar texto](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: está asociado a regiones que se pueden expandir o contraer en la esquematización.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: define el espacio que ocupa un elemento gráfico en una vista de texto. Para obtener más información sobre los elementos gráficos de negociación de espacios, vea la sección siguiente.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: proporciona el espaciado automático y el tamaño del elemento gráfico.

  Para buscar y usar etiquetas para búferes y vistas, importe <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> o <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , que proporcionan una <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> del tipo solicitado. En el código siguiente se importa este servicio como una propiedad.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Etiquetas y MarkerFormatDefinitions
 Puede extender la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> clase para definir el aspecto de una etiqueta. Debe exportar la clase (como un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nombre que se usa para hacer referencia a este formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Esto hace que el formato aparezca en la interfaz de usuario

  En el constructor, se define el nombre para mostrar y la apariencia de la etiqueta. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> define el color de relleno y <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> define el color del borde. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>Es el nombre traducible de la definición de formato.

  El siguiente es un ejemplo de una definición de formato:

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 Para aplicar esta definición de formato a una etiqueta, haga referencia al nombre establecido en el atributo name de la clase (no el nombre para mostrar).

> [!NOTE]
> Para obtener un ejemplo de <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , vea la clase HighlightWordFormatDefinition en [Tutorial: resaltar texto](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Extender elementos gráficos
 Los elementos gráficos definen efectos visuales que se pueden agregar al texto que se muestra en una vista de texto o a la propia vista de texto. Puede definir su propio elemento gráfico como cualquier tipo de <xref:System.Windows.UIElement> .

 En la clase de elemento gráfico, debe declarar <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Para registrar el nivel de elemento gráfico, expórtelo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del elemento gráfico.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: ordenación del elemento gráfico con respecto a otras capas de elementos gráficos. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> define cuatro niveles predeterminados: selección, esquematización, símbolo de intercalación y texto.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de capa de adornos.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Debe crear una segunda clase que implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> y controle su <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> evento creando una instancia del elemento gráfico. Debe exportar esta clase junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que es válido el elemento gráfico.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para el que este elemento gráfico es válido. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tiene el conjunto de roles de vista de texto predefinidos. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se usa principalmente para las vistas de texto de los archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se usa para las vistas de texto que un usuario puede editar o navegar mediante un mouse y un teclado. Ejemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> vistas son la vista de texto del editor y la ventana de **salida** .

  En el ejemplo siguiente se muestran los atributos de exportación en el proveedor de elementos gráficos.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un elemento gráfico de negociación de espacio es aquél que ocupa espacio en el mismo nivel que el texto. Para crear este tipo de elemento gráfico, debe definir una clase de etiqueta que herede de <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , que define la cantidad de espacio que ocupa el elemento gráfico.

 Como con todos los elementos gráficos, debe exportar la definición de la capa de adornos.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Para crear una instancia del elemento gráfico de negociación de espacios, debe crear una clase que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , además de la clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (como con otros tipos de elementos gráficos).

 Para registrar el proveedor del etiquetador, debe exportarlo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que es válido el elemento gráfico.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para el que esta etiqueta o elemento gráfico es válido. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tiene el conjunto de roles de vista de texto predefinidos. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se usa principalmente para las vistas de texto de los archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se usa para las vistas de texto que un usuario puede editar o navegar mediante un mouse y un teclado. Ejemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> vistas son la vista de texto del editor y la ventana de **salida** .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta o elemento gráfico que ha definido. Debe agregar un segundo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> para <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  En el ejemplo siguiente se muestran los atributos de exportación en el proveedor de etiquetadores para una etiqueta de gráfico de negociación de espacios.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Extender procesadores de mouse
 Puede Agregar un control especial para la entrada del mouse. Cree una clase que herede de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> e invalide los eventos del mouse para la entrada que desea controlar. También debe implementar <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> en una segunda clase y exportarla junto con el <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> que especifica el tipo de contenido (por ejemplo, "texto" o "código") para el que es válido el controlador del mouse.

 En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de procesador del mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Extender controladores de Drop
 Puede personalizar el comportamiento de los controladores de colocación para determinados tipos de texto mediante la creación de una clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> y una segunda clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> para crear el controlador de colocación. Debe exportar el controlador de colocación junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: formato de texto para el que este controlador de colocación es válido. Los siguientes formatos se controlan en orden de prioridad, de mayor a menor:

  1. Cualquier formato personalizado

  2. Entrega

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. DIF

  7. Configuración regional

  8. Paleta

  9. PenData

  10. Serializable

  11. SymbolicLink

  12. Lenguaje

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. DIB

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Formato HTML

  21. UnicodeText

  22. OEMText

  23. Texto

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del controlador de colocación.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden del controlador de colocación antes o después del controlador de eliminación predeterminado. El controlador de eliminación predeterminado para Visual Studio se denomina "DefaultFileDropHandler".

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de controlador de eliminación.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Extender las opciones del editor
 Puede definir opciones para que solo sean válidas en un determinado ámbito, por ejemplo, en una vista de texto. El editor proporciona este conjunto de opciones predefinidas: opciones del editor, opciones de vista y opciones de vista de Windows Presentation Foundation (WPF). Estas opciones se pueden encontrar en <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> y <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Para agregar una nueva opción, derive una clase de una de estas clases de definición de opción:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  En el ejemplo siguiente se muestra cómo exportar una definición de opción que tiene un valor booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Extender IntelliSense
 IntelliSense es un término general para un grupo de características que proporcionan información sobre el texto estructurado y la finalización de instrucciones. Estas características incluyen la finalización de instrucciones, la ayuda para las firmas, la información rápida y las bombillas. La finalización de instrucciones ayuda a los usuarios a escribir correctamente una palabra clave o un nombre de miembro de lenguaje. Ayuda para las firmas muestra la firma o las firmas para el método que acaba de escribir el usuario. Quick info muestra una firma completa para un nombre de tipo o miembro cuando el mouse se sitúa sobre él. Bombilla proporciona acciones adicionales para determinados identificadores en determinados contextos, por ejemplo, al cambiar el nombre de todas las apariciones de una variable después de que se haya cambiado el nombre de una aparición.

 El diseño de una característica de IntelliSense es muy similar en todos los casos:

- Un *agente* de IntelliSense es responsable del proceso global.

- Una *sesión* de IntelliSense representa la secuencia de eventos entre la activación del presentador y la confirmación o cancelación de la selección. Normalmente, el usuario desencadena la sesión.

- Un *controlador* de IntelliSense es responsable de decidir cuándo debe comenzar y finalizar la sesión. También decide cuándo se debe confirmar la información y cuándo se debe cancelar la sesión.

- Un *origen* de IntelliSense proporciona el contenido y decide cuál es la mejor coincidencia.

- Un *presentador* de IntelliSense es responsable de mostrar el contenido.

  En la mayoría de los casos, se recomienda proporcionar al menos un origen y un controlador. También puede proporcionar un presentador si desea personalizar la pantalla.

### <a name="implement-an-intellisense-source"></a>Implementar un origen de IntelliSense
 Para personalizar un origen, debe implementar una (o más) de las siguientes interfaces de origen:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> ha quedado en desuso en favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Además, debe implementar un proveedor de la misma clase:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> ha quedado en desuso en favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Debe exportar el proveedor junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del origen.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") al que se aplica el origen.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que debe aparecer el origen (con respecto a otros orígenes).

- En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de origen de finalización.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Para obtener más información sobre la implementación de orígenes de IntelliSense, vea los siguientes tutoriales:

- [Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Tutorial: Mostrar ayuda para las firmas](../extensibility/walkthrough-displaying-signature-help.md)

- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementar un controlador de IntelliSense
 Para personalizar un controlador, debe implementar la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfaz. Además, debe implementar un proveedor de controlador junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del controlador.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") al que se aplica el controlador.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que debe aparecer el controlador (con respecto a otros controladores).

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de controlador de finalización.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Para obtener más información sobre el uso de controladores de IntelliSense, vea los siguientes tutoriales:

- [Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
