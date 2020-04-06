---
title: Servicio de idiomas y puntos de extensión del editor ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703054"
---
# <a name="language-service-and-editor-extension-points"></a>Servicio de lenguaje y puntos de extensión del editor
El editor proporciona puntos de extensión que puede ampliar como componentes de Managed Extensibility Framework (MEF), incluidas la mayoría de las características del servicio de lenguaje. Estas son las principales categorías de puntos de extensión:

- Tipos de contenido

- Tipos de clasificación y formatos de clasificación

- Márgenes y barras de desplazamiento

- Etiquetas

- Adornos

- Procesadores de ratón

- Manipuladores de caídas

- Opciones

- IntelliSense

## <a name="extend-content-types"></a>Ampliar los tipos de contenido
 Los tipos de contenido son las definiciones de los tipos de texto controlados por el editor, por ejemplo, "texto", "código" o "CSharp". Para definir un nuevo tipo de contenido, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> declare una variable del tipo y asigne un nombre único al nuevo tipo. Para registrar el tipo de contenido con el editor, expórtelo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>es el nombre del tipo de contenido.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>es el nombre del tipo de contenido del que se deriva este tipo de contenido. Un tipo de contenido puede heredar de varios otros tipos de contenido.

  Dado <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> que la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de tipo de contenido.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Los tipos de contenido se pueden basar en cero o más tipos de contenido preexistentes. Estos son los tipos integrados:

- Cualquiera: el tipo de contenido básico. Padre de todos los demás tipos de contenido.

- Texto: el tipo básico para el contenido sin proyección. Hereda de "cualquiera".

- Texto sin formato: para texto sin código. Hereda de "texto".

- Código: para código de todo tipo. Hereda de "texto".

- Inerte: excluye el texto de cualquier tipo de manipulación. El texto de este tipo de contenido nunca tendrá ninguna extensión aplicada.

- Proyección: para el contenido de los búferes de proyección. Hereda de "cualquiera".

- Intellisense: para el contenido de IntelliSense. Hereda de "texto".

- Sighelp: ayuda de firma. Hereda de "intellisense".

- Sighelp-doc: documentación de ayuda de firma. Hereda de "intellisense".

  Estos son algunos de los tipos de contenido definidos por Visual Studio y algunos de los lenguajes que se hospedan en Visual Studio:

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

  Para detectar la lista de tipos <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>de contenido disponibles, importe el archivo , que mantiene la colección de tipos de contenido para el editor. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Para asociar un tipo de contenido <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>a una extensión de nombre de archivo, utilice .

> [!NOTE]
> En Visual Studio, las extensiones <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> de nombre de archivo se registran mediante el uso de un paquete de servicio de lenguaje. El <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> asocia un tipo de contenido MEF con una extensión de nombre de archivo que se ha registrado de esta manera.

 Para exportar la extensión de nombre de archivo a la definición de tipo de contenido, debe incluir los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: especifica la extensión de nombre de archivo.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: especifica el tipo de contenido.

  Dado <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación de una extensión de nombre de archivo a una definición de tipo de contenido.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 El <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> administra las asociaciones entre las extensiones de nombre de archivo y los tipos de contenido.

## <a name="extend-classification-types-and-classification-formats"></a>Ampliar los tipos de clasificación y los formatos de clasificación
 Puede utilizar tipos de clasificación para definir los tipos de texto para los que desea proporcionar un control diferente (por ejemplo, colorear el texto "palabra clave" en azul y el texto "comentario" verde). Defina un nuevo tipo de clasificación <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> declarando una variable de tipo y dándole un nombre único.

 Para registrar el tipo de clasificación con el editor, expórtelo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del tipo de clasificación.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: el nombre del tipo de clasificación del que hereda este tipo de clasificación. Todos los tipos de clasificación heredan de "texto" y un tipo de clasificación puede heredar de varios otros tipos de clasificación.

  Dado <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> que la clase está sellada, puede exportarla sin ningún parámetro de tipo.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de tipo de clasificación.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 El <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> proporciona acceso a clasificaciones estándar. Los tipos de clasificación integrados incluyen los siguientes:

- "text"

- "lenguaje natural" (deriva de "texto")

- "lenguaje formal" (deriva de "texto")

- "string" (deriva de "literal")

- "carácter" (deriva de "literal")

- "numérico" (deriva de "literal")

  Un conjunto de tipos <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>de error diferentes heredan de . Incluyen los siguientes tipos de error:

- "error de sintaxis"

- "error del compilador"

- "otro error"

- "Advertencia"

  Para detectar la lista de tipos <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>de clasificación disponibles, importe el archivo , que mantiene la colección de tipos de clasificación para el editor. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Puede definir una definición de formato de clasificación para el nuevo tipo de clasificación. Derive una <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> clase de y <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>expórtela con el tipo, junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: el nombre para mostrar del formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: especifica si el formato aparece en la página **Fuentes y colores** del cuadro de diálogo **Opciones.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la prioridad del formato. Los valores <xref:Microsoft.VisualStudio.Text.Classification.Priority>válidos son de .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: el nombre del tipo de clasificación al que se asigna este formato.

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

 Para descubrir la lista de <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>formatos disponibles, importe el archivo , que mantiene la colección de formatos para el editor. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Extender márgenes y barras de desplazamiento
 Los márgenes y las barras de desplazamiento son los elementos principales de la vista del editor, además de la propia vista de texto. Puede proporcionar cualquier número de márgenes además de los márgenes estándar que aparecen alrededor de la vista de texto.

 Implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> una interfaz para definir un margen. También debe implementar <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> la interfaz para crear el margen.

 Para registrar el proveedor de márgenes en el editor, debe exportar el proveedor junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del margen.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que aparece el margen, en relación con los demás márgenes.

   Estos son los márgenes incorporados:

  - "Barra de desplazamiento horizontal wpf"

  - "Barra de desplazamiento vertical wpf"

  - "Margen de número de línea wpf"

    Los márgenes horizontales que `After="Wpf Horizontal Scrollbar"` tienen un atributo de orden se muestran debajo del `Before ="Wpf Horizontal Scrollbar"` margen integrado y los márgenes horizontales que tienen un atributo de orden se muestran por encima del margen integrado. Los márgenes verticales derecho `After="Wpf Vertical Scrollbar"` que tienen un atributo order de se muestran a la derecha de la barra de desplazamiento. Los márgenes verticales izquierdos `After="Wpf Line Number Margin"` que tienen un atributo de orden aparecen a la izquierda del margen del número de línea (si está visible).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: el tipo de margen (izquierda, derecha, superior o inferior).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que su margen es válido.

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de margen para un margen que aparece a la derecha del margen del número de línea.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Extender etiquetas
 Las etiquetas son una forma de asociar datos con diferentes tipos de texto. En muchos casos, los datos asociados se muestran como un efecto visual, pero no todas las etiquetas tienen una presentación visual. Puede definir su propio tipo <xref:Microsoft.VisualStudio.Text.Tagging.ITag>de etiqueta implementando . También debe <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementar para proporcionar las etiquetas para un conjunto <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> determinado de intervalos de texto y un para proporcionar el etiquetador. Debe exportar el proveedor de etiquetas junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que su etiqueta es válida.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta.

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de etiqueta.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 Los siguientes tipos de etiqueta están integrados:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: asociado <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>a un archivo .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: asociado con tipos de error.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: asociado con un adorno.

  > [!NOTE]
  > Para obtener un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>ejemplo de un , vea la definición HighlightWordTag en [Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: asociado a regiones que se pueden expandir o contraer en la esquematización.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: define el espacio que ocupa un adorno en una vista de texto. Para obtener más información acerca de los adornos de negociación de espacio, consulte la sección siguiente.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: proporciona espaciado y tamaño automáticos para el adorno.

  Para buscar y utilizar etiquetas para búferes <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>y vistas, <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> importe el <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> , que le proporciona un tipo solicitado. El código siguiente importa este servicio como una propiedad.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Etiquetas y MarkerFormatDefinitions
 Puede ampliar <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> la clase para definir la apariencia de una etiqueta. Debe exportar la clase <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>(como a ) con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre utilizado para hacer referencia a este formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: esto hace que el formato aparezca en la interfaz de usuario

  En el constructor, se define el nombre para mostrar y la apariencia de la etiqueta. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>define el color <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> de relleno y define el color del borde. Es <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> el nombre localizable de la definición de formato.

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

 Para aplicar esta definición de formato a una etiqueta, haga referencia al nombre establecido en el atributo name de la clase (no al nombre para mostrar).

> [!NOTE]
> Para obtener un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>ejemplo de un , vea la clase HighlightWordFormatDefinition en [Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Extender adornos
 Los adornos definen efectos visuales que se pueden agregar al texto que se muestra en una vista de texto o a la propia vista de texto. Puede definir su propio adorno <xref:System.Windows.UIElement>como cualquier tipo de archivo .

 En la clase de adorno, debe declarar un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>archivo . Para registrar la capa de adorno, expórtela junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del adorno.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden del adorno con respecto a otras capas de adorno. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> clase define cuatro capas predeterminadas: Selección, Esquema, Intercalación y Texto.

  En el ejemplo siguiente se muestran los atributos de exportación en una definición de capa de adorno.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Debe crear una segunda clase <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> que <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> implemente y controle su evento creando instancias del adorno. Debe exportar esta clase junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que el adorno es válido.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para la que este adorno es válido. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> clase tiene el conjunto de roles de vista de texto predefinidos. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se utiliza principalmente para vistas de texto de archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>se utiliza para las vistas de texto que un usuario puede editar o navegar mediante un ratón y un teclado. Ejemplos <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> de vistas son la vista de texto del editor y la ventana **Salida.**

  En el ejemplo siguiente se muestran los atributos de exportación en el proveedor de adornos.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Un adorno de negociación de espacio es aquel que ocupa el espacio al mismo nivel que el texto. Para crear este tipo de adorno, debe definir <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>una clase de etiqueta que herede de , que define la cantidad de espacio que ocupa el adorno.

 Al igual que con todos los adornos, debe exportar la definición de capa de adorno.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Para crear una instancia del adorno de negociación <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>de espacio, debe crear <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> una clase que implemente, además de la clase que implementa (como con otros tipos de adornos).

 Para registrar el proveedor de etiquetas, debe exportarlo junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") para el que su adorno es válido.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para la que esta etiqueta o adorno es válido. La <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> clase tiene el conjunto de roles de vista de texto predefinidos. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se utiliza principalmente para vistas de texto de archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>se utiliza para las vistas de texto que un usuario puede editar o navegar mediante un ratón y un teclado. Ejemplos <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> de vistas son la vista de texto del editor y la ventana **Salida.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta o adorno que ha definido. Debe agregar un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>segundo para .

  En el ejemplo siguiente se muestran los atributos de exportación en el proveedor de etiqueta para una etiqueta de adorno de negociación de espacio.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Ampliación de los procesadores de ratón
 Puede agregar un control especial para la entrada del ratón. Cree una clase que <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> herede y reemplace los eventos del mouse para la entrada que desea controlar. También debe <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> implementar en una segunda clase <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> y exportarlo junto con el que especifica el tipo de contenido (por ejemplo, "texto" o "código") para el que el controlador del mouse es válido.

 En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de procesador de mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Extender los controladores de caída
 Puede personalizar el comportamiento de los controladores de colocación para <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> tipos específicos de <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> texto mediante la creación de una clase que implementa y una segunda clase que implementa para crear el controlador de colocación. Debe exportar el controlador de colocación junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: el formato de texto para el que este controlador de colocación es válido. Los siguientes formatos se gestionan en orden de prioridad de mayor a menor:

  1. Cualquier formato personalizado

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. Dif

  7. Configuración regional

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

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden del controlador de colocación antes o después del controlador de colocación predeterminado. El controlador de colocación predeterminado para Visual Studio se denomina "DefaultFileDropHandler".

  En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de controlador de colocación.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Ampliación de las opciones del editor
 Puede definir opciones para que sean válidas solo en un ámbito determinado, por ejemplo, en una vista de texto. El editor proporciona este conjunto de opciones predefinidas: opciones de editor, opciones de vista y opciones de vista de Windows Presentation Foundation (WPF). Estas opciones se <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>pueden <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>encontrar <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>en , , y .

 Para agregar una nueva opción, derive una clase de una de estas clases de definición de opciones:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  En el ejemplo siguiente se muestra cómo exportar una definición de opción que tiene un valor booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Ampliar IntelliSense
 IntelliSense es un término general para un grupo de características que proporcionan información sobre el texto estructurado y la finalización de instrucciones para él. Estas características incluyen la finalización de instrucciones, la ayuda de firma, la información rápida y las bombillas. La finalización de instrucciones ayuda a los usuarios a escribir correctamente una palabra clave de idioma o un nombre de miembro. La ayuda de firma muestra la firma o las firmas del método que el usuario acaba de escribir. Información rápida muestra una firma completa para un tipo o nombre de miembro cuando el mouse se apoya en él. La bombilla proporciona acciones adicionales para determinados identificadores en determinados contextos, por ejemplo, cambiar el nombre de todas las apariciones de una variable después de cambiar el nombre de una aparición.

 El diseño de una característica de IntelliSense es muy similar en todos los casos:

- Un *intermediario* de IntelliSense es responsable del proceso general.

- Una *sesión* de IntelliSense representa la secuencia de eventos entre la activación del presentador y la confirmación o cancelación de la selección. La sesión se desencadena normalmente por algún gesto del usuario.

- Un *controlador* IntelliSense es responsable de decidir cuándo debe iniciarse y finalizar la sesión. También decide cuándo se debe confirmar la información y cuándo se debe cancelar la sesión.

- Un *origen* de IntelliSense proporciona el contenido y decide la mejor coincidencia.

- Un *presentador* de IntelliSense es responsable de mostrar el contenido.

  En la mayoría de los casos, se recomienda proporcionar al menos un origen y un controlador. También puede proporcionar un presentador si desea personalizar la pantalla.

### <a name="implement-an-intellisense-source"></a>Implementar un origen de IntelliSense
 Para personalizar un origen, debe implementar una (o más) de las siguientes interfaces de origen:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>ha quedado en <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>desuso a favor de .

 Además, debe implementar un proveedor del mismo tipo:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>ha quedado en <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>desuso a favor de .

 Debe exportar el proveedor junto con los siguientes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre de la fuente.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "texto" o "código") al que se aplica la fuente.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que debe aparecer la fuente (con respecto a otras fuentes).

- En el ejemplo siguiente se muestran los atributos de exportación en un proveedor de origen de finalización.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Para obtener más información acerca de la implementación de orígenes de IntelliSense, consulte los siguientes tutoriales:

- [Tutorial: Mostrar información sobre herramientas quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Tutorial: Mostrar la Ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementar un controlador IntelliSense
 Para personalizar un controlador, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> debe implementar la interfaz. Además, debe implementar un proveedor de controlador junto con los siguientes atributos:

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

 Para obtener más información acerca del uso de controladores IntelliSense, consulte los siguientes tutoriales:

- [Tutorial: Mostrar información sobre herramientas quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
