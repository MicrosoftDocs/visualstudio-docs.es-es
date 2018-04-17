---
title: Servicio de lenguaje y puntos de extensión del Editor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c253ba52da1fd6bb9133e44ba6858e8f1a4151
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="language-service-and-editor-extension-points"></a>Servicio de lenguaje y puntos de extensión del Editor
El editor proporciona puntos de extensión que puede extender como componentes de Managed Extensibility Framework (MEF), incluidas las características de servicio de lenguaje mayoría. Estas son las categorías de punto de extensión principal:  
  
-   Tipos de contenido  
  
-   Tipos de clasificación y formatos de clasificación  
  
-   Los márgenes y las barras de desplazamiento  
  
-   Etiquetas  
  
-   Opciones gráficas  
  
-   Procesadores de mouse (ratón)  
  
-   Quitar controladores  
  
-   Opciones  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Extender tipos de contenido  
 Tipos de contenido son las definiciones de los tipos de texto que se administra mediante el editor, por ejemplo, "text", "código" o "CSharp". Definir un nuevo tipo de contenido al declarar una variable del tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> y que proporciona el nuevo tipo de contenido de un nombre único. Para registrar el tipo de contenido con el editor, exportarlo junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> es el nombre del tipo de contenido.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> es el nombre del tipo de contenido que se deriva este tipo de contenido. Un tipo de contenido puede heredar de varios otros tipos de contenido.  
  
 Dado que la <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> es una clase sealed, puede exportarlo con ningún parámetro de tipo.  
  
 El ejemplo siguiente muestra los atributos de exportación en una definición de tipo de contenido.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Tipos de contenido pueden basarse en cero o más tipos de contenido ya existentes. Estos son los tipos integrados:  
  
-   Ninguno: el tipo de contenido básico. Elemento primario de todos los demás tipos de contenido.  
  
-   Texto: el tipo básico de proyección no contenido. Hereda de "cualquiera".  
  
-   Texto simple: para el texto del código. Hereda de "text".  
  
-   Código: para el código de todos los tipos. Hereda de "text".  
  
-   Inerte: excluye el texto de cualquier tipo de control. Texto de este tipo de contenido nunca tendrá cualquier extensión aplicada a él.  
  
-   Proyección: para el contenido de los búferes de proyección. Hereda de "cualquiera".  
  
-   IntelliSense: para el contenido de IntelliSense. Hereda de "text".  
  
-   Sighelp: ayuda para las firmas. Hereda de "intellisense".  
  
-   Sighelp-doc: documentación de ayuda firma. Hereda de "intellisense".  
  
 Estos son algunos de los tipos de contenido que se definen mediante Visual Studio y algunos de los idiomas que se hospedan en Visual Studio:  
  
-   Básico  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Para conocer la lista de tipos de contenido disponibles, importar el <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, que mantiene la colección de tipos de contenido para el editor. El siguiente código importa este servicio como una propiedad.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Para asociar un tipo de contenido a una extensión de nombre de archivo, use <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  En Visual Studio, se registran las extensiones de nombre de archivo mediante el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> en un paquete de servicio de lenguaje. El <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> asocia un tipo de contenido de MEF con una extensión de nombre de archivo que se ha registrado de esta manera.  
  
 Para exportar la extensión de nombre de archivo a la definición de tipo de contenido, debe incluir los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: especifica la extensión de nombre de archivo.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: especifica el tipo de contenido.  
  
 Dado que la <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> es una clase sealed, puede exportarlo con ningún parámetro de tipo.  
  
 El ejemplo siguiente muestra los atributos de exportación en una extensión de nombre de archivo a una definición de tipo de contenido.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 El <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> administra las asociaciones entre las extensiones de nombre de archivo y los tipos de contenido.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Da formato a extender clasificación y tipos de clasificación  
 Puede usar tipos de clasificación para definir los tipos de texto para el que desea proporcionar un tratamiento distinto (por ejemplo, el color del texto de "la palabra clave" azul y el texto "comment" verde). Definir un nuevo tipo de clasificación al declarar una variable de tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> y se le asigna un nombre único.  
  
 Para registrar el tipo de clasificación con el editor, exportarlo junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del tipo de clasificación.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: el nombre del tipo de clasificación de la que hereda este tipo de clasificación. Heredan de todos los tipos de clasificación de "text" y un tipo de clasificación puede heredar de varios otros tipos de clasificación.  
  
 Dado que la <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> es una clase sealed, puede exportarlo con ningún parámetro de tipo.  
  
 El ejemplo siguiente muestra los atributos de exportación en una definición de tipo de clasificación.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 El <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> proporciona acceso a las clasificaciones estándar. Tipos de clasificación integradas son:  
  
-   "texto"  
  
-   "lenguaje natural" (que se deriva de "text")  
  
-   "lenguaje formal" (que se deriva de "text")  
  
-   "cadena" (que se deriva de "literal")  
  
-   "character" (que se deriva de "literal")  
  
-   "numérico" (que se deriva de "literal")  
  
 Heredar de un conjunto de distintos tipos de error de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Incluyen los siguientes tipos de error:  
  
-   "error de sintaxis"  
  
-   "error del compilador"  
  
-   "error"  
  
-   "Advertencia"  
  
 Para conocer la lista de tipos de clasificación disponibles, importar el <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, que mantiene la colección de tipos de clasificación para el editor. El siguiente código importa este servicio como una propiedad.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Puede crear una definición de formato de clasificación para el nuevo tipo de clasificación. Derivar una clase de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> y se exporta con el tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del formato.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: el nombre para mostrar del formato.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Especifica si el formato aparece en el **fuentes y colores** página de la **opciones** cuadro de diálogo.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la prioridad del formato. Los valores válidos son de <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: el nombre de la clasificación de tipo al que está asignado este formato.  
  
 El ejemplo siguiente muestra los atributos de exportación en una definición de formato de clasificación.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Para detectar la lista de formatos disponibles, importar el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, que mantiene la colección de formatos para el editor. El siguiente código importa este servicio como una propiedad.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Barras de desplazamiento y cómo se extienden los márgenes  
 Los márgenes y las barras de desplazamiento son los elementos de la vista principal del editor además de la propia vista de texto. Puede proporcionar cualquier número de márgenes, además de los márgenes estándares que aparecen alrededor de la vista de texto.  
  
 Implemente un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfaz para definir un margen. También debe implementar la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaz para crear el margen.  
  
 Para registrar el proveedor de margen con el editor, debe exportar el proveedor junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del margen.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que aparece el margen con respecto a los márgenes de otros.  
  
     Estos son los márgenes integrados:  
  
    -   "Barra de desplazamiento Horizontal de Wpf"  
  
    -   "Barra de desplazamiento Vertical de Wpf"  
  
    -   "Margen del número de línea de Wpf"  
  
     Los márgenes horizontales que tienen un atributo de orden de `After="Wpf Horizontal Scrollbar"` se muestran a continuación el margen integrado y los márgenes horizontales que tienen un atributo de orden de `Before ="Wpf Horizontal Scrollbar"` se muestran sobre el margen integrado. Haga los márgenes verticales que tienen un atributo de orden de `After="Wpf Vertical Scrollbar"` se muestran a la derecha de la barra de desplazamiento. Deja los márgenes verticales que tienen un atributo de orden de `After="Wpf Line Number Margin"` aparecen a la izquierda del margen de número de línea (si está visible).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: el tipo de margen (izquierda, derecha, arriba o abajo).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") para el que el margen es válido.  
  
 El ejemplo siguiente muestra los atributos de exportación en un proveedor de margen para el margen situado a la derecha del margen de número de línea.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Extender las etiquetas  
 Las etiquetas son una manera de asociar datos con distintos tipos de texto. En muchos casos, los datos asociados se muestran como un efecto visual posible, pero no todas las etiquetas tienen una presentación visual. Puede definir su propio tipo de etiqueta mediante la implementación de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. También debe implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> para proporcionar las etiquetas para un determinado conjunto de intervalos de texto y un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> para proporcionar el etiquetador. Debe exportar el proveedor del etiquetador junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") para que la etiqueta sea válida.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta.  
  
 El ejemplo siguiente muestra los atributos de exportación en un proveedor del etiquetador.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Los siguientes tipos de etiqueta están integrados:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: asociado con un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: asociadas con los tipos de error.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: asociada a un elemento de gráfico.  
  
    > [!NOTE]
    >  Para obtener un ejemplo de un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, consulte la definición de HighlightWordTag de [Tutorial: texto resaltado](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: asociados a las regiones que pueden expandir o contraer en la esquematización.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: define el espacio que ocupa un elemento de gráfico en una vista de texto. Para obtener más información sobre el gráfico de negociación de espacio, vea la sección siguiente.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: proporciona el espaciado automático y ajuste de tamaño para el elemento de gráfico.  
  
 Para buscar y usar etiquetas para los búferes y las vistas, importar la <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> o <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, que proporcionan un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> del tipo solicitado. El siguiente código importa este servicio como una propiedad.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Las etiquetas y MarkerFormatDefinitions  
 Puede ampliar el <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> clase para definir la apariencia de una etiqueta. Debe exportar la clase (como un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre utilizado para hacer referencia a este formato  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Esto hace que el formato que aparecen en la interfaz de usuario  
  
 En el constructor, defina el nombre para mostrar y la apariencia de la etiqueta. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> define el color de relleno, y <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> define el color del borde. El <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> es el nombre de la definición de formato localizable.  
  
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
  
 Para aplicar esta definición de formato a una etiqueta, hacer referencia al nombre que se establece en el atributo de nombre de la clase (no el nombre para mostrar).  
  
> [!NOTE]
>  Para obtener un ejemplo de un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, vea la clase HighlightWordFormatDefinition en [Tutorial: texto resaltado](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Extender opciones gráficas  
 Opciones gráficas definen efectos visuales que pueden agregarse al texto que se muestra en una vista de texto o al texto ver propio. Puede definir sus propios elementos de gráficos como cualquier tipo de <xref:System.Windows.UIElement>.  
  
 En la clase de elemento gráfico, debe declarar un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Para registrar el nivel del elemento gráfico, exportarlo junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del elemento gráfico.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden de los elementos de gráficos con respecto a otras capas de elementos gráficos. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> define cuatro niveles de manera predeterminada: selección, esquematización, símbolo de intercalación y texto.  
  
 El ejemplo siguiente muestra los atributos de exportación en una definición de la capa de elementos gráficos.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Debe crear una segunda clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> y controla su <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> eventos creando instancias de los elementos de gráficos. Debe exportar esta clase junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") para el que el elemento de gráfico es válido.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para el que este elemento de gráfico es válido. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tiene el conjunto de roles de la vista de texto predefinido. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se utiliza principalmente para las vistas de texto de archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se utiliza para las vistas de texto que un usuario puede editar o navegar mediante un mouse y teclado. Ejemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> vistas son la vista de editor de texto y el **salida** ventana.  
  
 El ejemplo siguiente muestra los atributos de exportación en el proveedor de elementos gráficos.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Un elemento de gráfico de negociación de espacio es aquel que ocupa espacio en el mismo nivel que el texto. Para crear este tipo de elemento gráfico, debe definir una clase de etiqueta que hereda de <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, que define la cantidad de espacio que ocupa el elemento de gráfico.  
  
 Al igual que con todos los elementos de gráficos, debe exportar la definición de la capa de elementos gráficos.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Para crear una instancia del elemento de gráfico de negociación de espacio, debe crear una clase que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, además de la clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (al igual que con otros tipos de elementos gráficos).  
  
 Para registrar el proveedor del etiquetador, debe exportarlo junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") para el que el elemento de gráfico es válido.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: el tipo de vista de texto para el que este elemento gráfico o la etiqueta es válida. La clase <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tiene el conjunto de roles de la vista de texto predefinido. Por ejemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se utiliza principalmente para las vistas de texto de archivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se utiliza para las vistas de texto que un usuario puede editar o navegar mediante un mouse y teclado. Ejemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> vistas son la vista de editor de texto y el **salida** ventana.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: el tipo de etiqueta o elementos gráficos que haya definido. Debe agregar un segundo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> para <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 El ejemplo siguiente muestra los atributos de exportación en el proveedor del etiquetador de una etiqueta de elemento gráfico de negociación de espacios.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Extender procesadores de mouse (ratón)  
 Puede agregar un control especial para la entrada del mouse. Cree una clase que hereda de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> e invalidar los eventos del mouse para la entrada que desea controlar. También debe implementar <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> en una segunda clase y exportarlo junto con el <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> que especifica el tipo de contenido (por ejemplo, "text" o "code") para el que el controlador de mouse (ratón) es válido.  
  
 El ejemplo siguiente muestra los atributos de exportación en un proveedor de procesador de mouse (ratón).  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Extender controladores de colocación  
 Puede personalizar el comportamiento de controladores de colocación para determinados tipos de texto mediante la creación de una clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> y una segunda clase que implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> para crear el controlador de colocación. Debe exportar el controlador de colocación junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: el formato de texto para el que este controlador de eliminación es válido. Los formatos siguientes se tratan en orden de prioridad de mayor a menor:  
  
    1.  Cualquier formato personalizado  
  
    2.  Entrega de archivos  
  
    3.  EnhancedMetafile  
  
    4.  Onda de sonido  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Configuración regional  
  
    8.  Paleta  
  
    9. PenData  
  
    10. Serializable  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. Formato HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Texto  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del controlador de colocación.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden del controlador de colocar antes o después del controlador de colocar de forma predeterminada. El controlador de destino predeterminado para Visual Studio se denomina "DefaultFileDropHandler".  
  
 El ejemplo siguiente muestra los atributos de exportación en un proveedor del controlador de colocación.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Extensión de opciones del Editor  
 Puede definir opciones para ser válido solo en un cierto ámbito, por ejemplo, en una vista de texto. El editor proporciona este conjunto de opciones predefinidas: opciones del editor, vea las opciones y opciones de la vista de Windows Presentation Foundation (WPF). Estas opciones se pueden encontrar en <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, y <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Para agregar una nueva opción, derive una clase de una de estas clases de definición de la opción:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 En el ejemplo siguiente se muestra cómo exportar una definición de la opción que tiene un valor booleano.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Extender IntelliSense  
 IntelliSense es un término general para un grupo de características que proporcionan información acerca de texto estructurados y finalización de instrucciones para él. Estas características incluyen la finalización de instrucciones, ayuda para las firmas, información rápida y las bombillas. Finalización de instrucciones ayuda a los usuarios escribir un nombre de palabra clave o un miembro de idioma correctamente. Ayuda para las firmas muestra la firma o firmas para el método que el usuario solo tiene un tipo. Información rápida muestra una firma completa para un nombre de tipo o miembro cuando el mouse se sitúa en él. Bombilla proporcionar acciones adicionales para determinados identificadores en ciertos contextos, por ejemplo, cambiar el nombre de todas las apariciones de una variable después de que se ha cambiado el nombre de una ocurrencia.  
  
 El diseño de una característica IntelliSense es el mismo en todos los casos:  
  
-   Un IntelliSense *broker* es responsable del proceso general.  
  
-   Un IntelliSense *sesión* representa la secuencia de eventos entre la activación de moderador y la confirmación o cancelación de la selección. Algunos gesto de usuario normalmente desencadena la sesión.  
  
-   Un IntelliSense *controlador* es responsable de decidir cuándo debe empezar y terminar la sesión. También decide cuándo se debería confirmar la información y cuándo se debe cancelar la sesión.  
  
-   Un IntelliSense *origen* proporciona el contenido y decide la mejor coincidencia.  
  
-   Un IntelliSense *presentador* es responsable de mostrar el contenido.  
  
 En la mayoría de los casos, se recomienda que proporcione al menos un origen y un controlador. También puede proporcionar un presentador si desea personalizar la presentación.  
  
### <a name="implementing-an-intellisense-source"></a>Implementación de un origen de IntelliSense  
 Para personalizar un origen, debe implementar uno (o más) de las interfaces de origen siguientes:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> está desusado en favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Además, debe implementar un proveedor de la misma clase:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> está desusado en favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Debe exportar el proveedor junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del origen.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") al que se aplica el origen.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que debe aparecer el origen (con respecto a otros orígenes).  
  
-   El ejemplo siguiente muestra los atributos de exportación en un proveedor de código fuente de finalización.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Para obtener más información acerca de cómo implementar orígenes de IntelliSense, vea los siguientes tutoriales:  
  
 [Tutorial: visualización de información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Tutorial: visualización de la ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementar un controlador de IntelliSense  
 Para personalizar un controlador, debe implementar la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfaz. Además, debe implementar un proveedor de controlador junto con los siguientes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: el nombre del controlador.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: el tipo de contenido (por ejemplo, "text" o "code") al que se aplica el controlador.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: el orden en el que debe aparecer el controlador (con respecto a otros controladores).  
  
 El ejemplo siguiente muestra los atributos de exportación en un proveedor del controlador de finalización.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Para obtener más información sobre el uso de controladores de IntelliSense, vea los siguientes tutoriales:  
  
 [Tutorial: visualización de información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)