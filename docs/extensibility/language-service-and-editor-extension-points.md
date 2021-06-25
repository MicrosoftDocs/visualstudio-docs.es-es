---
title: Servicios de lenguaje y puntos de extensión del editor | Microsoft Docs
description: Obtenga información sobre los puntos de extensión en el editor Visual Studio código que puede ampliar, incluida la mayoría de las características del servicio de lenguaje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 293851f1f3e72508a9bc119fb7551b0118ab2a9b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903152"
---
# <a name="language-service-and-editor-extension-points"></a>Puntos de extensión del editor y el servicio de lenguaje
El editor proporciona puntos de extensión que puede extender como componentes Managed Extensibility Framework componentes (MEF), incluida la mayoría de las características del servicio de lenguaje. Estas son las categorías principales de punto de extensión:

- Tipos de contenido

- Tipos de clasificación y formatos de clasificación

- Márgenes y barras de desplazamiento

- Etiquetas

- Adornos

- Procesadores de mouse

- Controladores de colocación

- Opciones

- IntelliSense

## <a name="extend-content-types"></a>Extensión de tipos de contenido
 Los tipos de contenido son las definiciones de los tipos de texto que controla el editor, por ejemplo, "text", "code" o "CSharp". Para definir un nuevo tipo de contenido, declare una variable del tipo y asigne un nombre único al nuevo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> tipo de contenido. Para registrar el tipo de contenido con el editor, exporte junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> es el nombre del tipo de contenido.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> es el nombre del tipo de contenido del que se deriva este tipo de contenido. Un tipo de contenido puede heredar de varios otros tipos de contenido.

  Dado que <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de tipo de contenido.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Los tipos de contenido pueden basarse en cero o más tipos de contenido existentes. Estos son los tipos integrados:

- Cualquiera: el tipo de contenido básico. Elemento primario de todos los demás tipos de contenido.

- Texto: el tipo básico para el contenido que no es de proyección. Hereda de "any".

- Texto sin formato: para texto que no es de código. Hereda de "text".

- Código: para código de todo tipo. Hereda de "text".

- Inert: excluye el texto de cualquier tipo de control. El texto de este tipo de contenido nunca tendrá ninguna extensión aplicada.

- Proyección: para el contenido de los búferes de proyección. Hereda de "any".

- IntelliSense: para el contenido de IntelliSense. Hereda de "text".

- Sighelp: ayuda de firma. Hereda de "IntelliSense".

- Sighelp-doc: documentación de ayuda de firma. Hereda de "IntelliSense".

  Estos son algunos de los tipos de contenido definidos por Visual Studio y algunos de los idiomas que se hospedan en Visual Studio:

- Básico

- C/C++

- ConsoleOutput

- CSharp

- CSS

- Enc

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Para detectar la lista de tipos de contenido disponibles, importe <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , que mantiene la colección de tipos de contenido para el editor. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Para asociar un tipo de contenido a una extensión de nombre de archivo, use <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> En Visual Studio, las extensiones de nombre de archivo se registran mediante en <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> un paquete de servicio de lenguaje. asocia <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> un tipo de contenido MEF a una extensión de nombre de archivo que se ha registrado de esta manera.

 Para exportar la extensión de nombre de archivo a la definición de tipo de contenido, debe incluir los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: especifica la extensión de nombre de archivo.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: especifica el tipo de contenido.

  Dado que <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación de una extensión de nombre de archivo a una definición de tipo de contenido.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 administra <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> las asociaciones entre las extensiones de nombre de archivo y los tipos de contenido.

## <a name="extend-classification-types-and-classification-formats"></a>Ampliación de los tipos de clasificación y los formatos de clasificación
 Puede usar tipos de clasificación para definir los tipos de texto para los que desea proporcionar un control diferente (por ejemplo, coloreando el texto "palabra clave" azul y el texto "comentario" verde). Defina un nuevo tipo de clasificación declarando una variable de tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> y asínándole un nombre único.

 Para registrar el tipo de clasificación con el editor, exporte junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del tipo de clasificación.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nombre del tipo de clasificación del que hereda este tipo de clasificación. Todos los tipos de clasificación heredan de "text" y un tipo de clasificación puede heredar de otros tipos de clasificación.

  Dado que <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de tipo de clasificación.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 proporciona <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> acceso a las clasificaciones estándar. Los tipos de clasificación integrados incluyen los siguientes:

- "text"

- "lenguaje natural" (se deriva de "texto")

- "lenguaje formal" (se deriva de "text")

- "string" (se deriva de "literal")

- "character" (se deriva de "literal")

- "numerical" (se deriva de "literal")

  Un conjunto de tipos de error diferentes heredan de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Incluyen los siguientes tipos de error:

- "error de sintaxis"

- "error del compilador"

- "otro error"

- "warning"

  Para detectar la lista de tipos de clasificación disponibles, importe <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , que mantiene la colección de tipos de clasificación para el editor. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Puede definir una definición de formato de clasificación para el nuevo tipo de clasificación. Derive una clase de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> y exporte con el tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> , junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nombre del formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: el nombre para mostrar del formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: especifica si el formato aparece en la página **Fuentes y colores** del cuadro de **diálogo** Opciones .

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la prioridad del formato. Los valores válidos son de <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nombre del tipo de clasificación al que está asignado este formato.

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

 Para detectar la lista de formatos disponibles, importe <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , que mantiene la colección de formatos para el editor. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Ampliación de márgenes y barras de desplazamiento
 Los márgenes y las barras de desplazamiento son los elementos de vista principales del editor, además de la propia vista de texto. Puede proporcionar cualquier número de márgenes además de los márgenes estándar que aparecen alrededor de la vista de texto.

 Implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> una interfaz para definir un margen. También debe implementar la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz para crear el margen.

 Para registrar el proveedor de márgenes con el editor, debe exportar el proveedor junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nombre del margen.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que aparece el margen, con respecto a los demás márgenes.

   Estos son los márgenes integrados:

  - "Barra de desplazamiento horizontal de Wpf"

  - "Barra de desplazamiento vertical de Wpf"

  - "Margen de número de línea de Wpf"

    Los márgenes horizontales que tienen un atributo order de se muestran debajo del margen integrado y los márgenes horizontales que tienen un atributo order de se muestran encima del margen `After="Wpf Horizontal Scrollbar"` `Before ="Wpf Horizontal Scrollbar"` integrado. Los márgenes verticales derecho que tienen un atributo order de `After="Wpf Vertical Scrollbar"` se muestran a la derecha de la barra de desplazamiento. Los márgenes verticales izquierdos que tienen un atributo order de aparecen a la izquierda del margen de número de `After="Wpf Line Number Margin"` línea (si está visible).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: el tipo de margen (izquierda, derecha, superior o inferior).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que el margen es válido.

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de márgenes para un margen que aparece a la derecha del margen de número de línea.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Extender etiquetas
 Las etiquetas son una manera de asociar datos con diferentes tipos de texto. En muchos casos, los datos asociados se muestran como un efecto visual, pero no todas las etiquetas tienen una presentación visual. Puede definir su propio tipo de etiqueta implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . También debe implementar para proporcionar las etiquetas para un conjunto determinado de intervalos de texto y para <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> proporcionar el etiquetador. Debe exportar el proveedor de etiquetas junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") para el que la etiqueta es válida.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta.

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de etiquetador.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> Los siguientes tipos de etiquetas están integrados:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: asociado a <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> un objeto .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: asociado a tipos de error.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: asociado a un adorno.

  > [!NOTE]
  > Para obtener un ejemplo de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , vea la definición HighlightWordTag [en Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: asociado a regiones que se pueden expandir o contraer en la delineación.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: define el espacio que ocupa un adorno en una vista de texto. Para obtener más información sobre los adornos de negociación de espacio, vea la sección siguiente.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: proporciona espaciado automático y ajuste de tamaño para el adorno.

  Para buscar y usar etiquetas para búferes y vistas, importe o , que <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> le ofrecen un del tipo <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> solicitado. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tags y MarkerFormatDefinitions
 Puede extender la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> clase para definir la apariencia de una etiqueta. Debe exportar la clase (como <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre usado para hacer referencia a este formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: esto hace que el formato aparezca en la interfaz de usuario

  En el constructor, defina el nombre para mostrar y la apariencia de la etiqueta. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> define el color de relleno y <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> el color del borde. es <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> el nombre localizable de la definición de formato.

  A continuación se muestra un ejemplo de una definición de formato:

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

 Para aplicar esta definición de formato a una etiqueta, haga referencia al nombre que estableció en el atributo name de la clase (no en el nombre para mostrar).

> [!NOTE]
> Para obtener un ejemplo de <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , vea la clase HighlightWordFormatDefinition en [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Ampliar adornos
 Los adornos definen efectos visuales que se pueden agregar al texto que se muestra en una vista de texto o a la propia vista de texto. Puede definir su propio adorno como cualquier tipo de <xref:System.Windows.UIElement> .

 En la clase de adorno, debe declarar <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Para registrar la capa de adorno, exporte junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del adorno.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden del adorno con respecto a otras capas de adorno. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> define cuatro capas predeterminadas: Selección, Esquemat, Símbolo de referencia y Texto.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de capa de adorno.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Debe crear una segunda clase que implemente y controle su evento mediante la creación de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> instancias del adorno. Debe exportar esta clase junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") para el que el adorno es válido.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para el que este adorno es válido. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tiene el conjunto de roles de vista de texto predefinidos. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se usa principalmente para vistas de texto de archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se usa para las vistas de texto que un usuario puede editar o navegar mediante un mouse y un teclado. Algunos ejemplos <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> de vistas son la vista de texto del editor y la **ventana** Salida.

  En el ejemplo siguiente se muestran los atributos de exportación en el proveedor de adornos.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un adorno de negociación de espacio es aquel que ocupa espacio en el mismo nivel que el texto. Para crear este tipo de adorno, debe definir una clase de etiqueta que herede de , que define la cantidad de espacio que <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> ocupa el adorno.

 Al igual que con todos los adornos, debe exportar la definición de la capa de adornos.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Para crear una instancia del adorno de negociación de espacio, debe crear una clase que implemente , además de la clase que implementa (como con otros tipos de <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> adornos).

 Para registrar el proveedor de etiquetas, debe exportarlo junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que el adorno es válido.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para el que esta etiqueta o adorno es válido. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tiene el conjunto de roles de vista de texto predefinidos. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se usa principalmente para vistas de texto de archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se usa para las vistas de texto que un usuario puede editar o navegar mediante un mouse y un teclado. Algunos ejemplos <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> de vistas son la vista de texto del editor y la **ventana** Salida.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta o adorno que ha definido. Debe agregar un segundo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> para <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  En el ejemplo siguiente se muestran los atributos de exportación en el proveedor de etiquetas para una etiqueta de adorno de negociación de espacio.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Extender procesadores de mouse
 Puede agregar un control especial para la entrada del mouse. Cree una clase que herede de e invalide los eventos del <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> mouse para la entrada que desea controlar. También debe implementar en una segunda clase y exportarla junto con el que especifica el tipo de contenido <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> (por ejemplo, "texto" o "código") para el que el controlador del <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> mouse es válido.

 En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de procesadores de mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Extender controladores de colocación
 Puede personalizar el comportamiento de los controladores de colocación para tipos específicos de texto mediante la creación de una clase que implementa y una segunda clase que implementa para crear <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> el controlador de colocación. Debe exportar el controlador de colocación junto con los atributos siguientes:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: el formato de texto para el que este controlador de colocación es válido. Los siguientes formatos se controlan en orden de prioridad de mayor a menor:

  1. Cualquier formato personalizado

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. Dif

  7. Locale

  8. Paleta

  9. PenData

  10. Serializable

  11. SymbolicLink

  12. Xaml

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Formato HTML

  21. UnicodeText

  22. OEMText

  23. Texto

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del controlador de colocación.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la ordenación del controlador de colocación antes o después del controlador de colocación predeterminado. El controlador de colocación predeterminado Visual Studio se denomina "DefaultFileDropHandler".

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de controladores de colocación.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Extender las opciones del editor
 Puede definir opciones para que sean válidas solo en un ámbito determinado, por ejemplo, en una vista de texto. El editor proporciona este conjunto de opciones predefinidas: opciones del editor, opciones de vista y opciones de Windows Presentation Foundation (WPF). Estas opciones se pueden encontrar <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> en <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> , y <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Para agregar una nueva opción, derive una clase de una de estas clases de definición de opción:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  En el ejemplo siguiente se muestra cómo exportar una definición de opción que tiene un valor booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Extensión de IntelliSense
 IntelliSense es un término general para un grupo de características que proporcionan información sobre el texto estructurado y la finalización de instrucciones para él. Estas características incluyen la finalización de instrucciones, la ayuda de firma, la información rápida y las bombillas. La finalización de instrucciones ayuda a los usuarios a escribir correctamente una palabra clave de lenguaje o un nombre de miembro. La Ayuda para la firma muestra la firma o las firmas del método que el usuario acaba de escribir. Información rápida muestra una firma completa para un tipo o nombre de miembro cuando el mouse está sobre él. La bombilla proporciona acciones adicionales para determinados identificadores en determinados contextos, por ejemplo, cambiar el nombre de todas las apariciones de una variable después de cambiar el nombre de una repetición.

 El diseño de una característica de IntelliSense es muy similar en todos los casos:

- Un agente *de* IntelliSense es responsable del proceso general.

- Una sesión *de* IntelliSense representa la secuencia de eventos entre el desencadenamiento del presentador y la confirmación o cancelación de la selección. La sesión se desencadena normalmente mediante algún gesto del usuario.

- Un controlador *de* IntelliSense es responsable de decidir cuándo debe iniciarse y finalizar la sesión. También decide cuándo se debe confirma la información y cuándo se debe cancelar la sesión.

- Un origen *de* IntelliSense proporciona el contenido y decide la mejor coincidencia.

- Un *presentador de* IntelliSense es responsable de mostrar el contenido.

  En la mayoría de los casos, se recomienda proporcionar al menos un origen y un controlador. También puede proporcionar un presentador si desea personalizar la pantalla.

### <a name="implement-an-intellisense-source"></a>Implementar un origen de IntelliSense
 Para personalizar un origen, debe implementar una (o varias) de las interfaces de origen siguientes:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> ha quedado en desuso en favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Además, debe implementar un proveedor del mismo tipo:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> ha quedado en desuso en favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Debe exportar el proveedor junto con los atributos siguientes:

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

 Para obtener más información sobre cómo implementar orígenes de IntelliSense, vea los tutoriales siguientes:

- [Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Tutorial: Mostrar la Ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementación de un controlador de IntelliSense
 Para personalizar un controlador, debe implementar la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfaz . Además, debe implementar un proveedor de controlador junto con los atributos siguientes:

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

 Para obtener más información sobre el uso de controladores de IntelliSense, vea los tutoriales siguientes:

- [Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
