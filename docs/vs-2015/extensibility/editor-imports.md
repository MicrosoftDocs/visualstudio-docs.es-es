---
title: Importaciones del Editor | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7017d4a99bbfd58a854ba1cd33230f11928024cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582213"
---
# <a name="editor-imports"></a>Importaciones del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [importaciones del Editor](https://docs.microsoft.com/visualstudio/extensibility/editor-imports).  
  
Puede importar un número de servicios del editor, generadores y agentes que proporcionan la extensión con distintos tipos de acceso para el editor básico. Por ejemplo, puede importar el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> para proporcionarle un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> para un tipo de contenido determinado. (Este navegador permite que realizar diferentes tipos de búsquedas en un búfer de texto).  
  
 Para usar una importación de editor, importarla como un campo o propiedad de una clase que se exporta una parte del componente de Managed Extensibility Framework.  
  
> [!NOTE]
>  Para obtener más información acerca de Managed Extensibility Framework, vea [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Sintaxis de importación  
 El ejemplo siguiente muestra cómo importar el editor de servicio de generador de opciones.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Si desea importar el servicio como un campo y no una propiedad, debe establecer en `null` en la declaración con el fin de evitar las advertencias del compilador acerca de cómo no asignar a una variable:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Para obtener más ejemplos del uso de las importaciones, vea los siguientes tutoriales:  
  
 [Tutorial: creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Tutorial: personalización de la vista de texto](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Tutorial: destacado de texto](../extensibility/walkthrough-highlighting-text.md)  
  
 [Tutorial: visualización de información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Tutorial: visualización de la ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Tutorial: Mostrar etiquetas inteligentes](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Importar el proveedor de servicios  
 También puede importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (que se encuentra en el ensamblado Microsoft.VisualStudio.Shell.Immutable.10.0) de la misma manera para obtener acceso a los servicios de Visual Studio:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Consulte [Tutorial: acceso al objeto DTE desde una extensión del Editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) para obtener más información.  
  
## <a name="services"></a>Servicios  
 Editor de servicios es generalmente sola entidades que proporcionan un servicio y se comparten entre varios componentes.  
  
|Importar|Proporciona|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relación entre las extensiones de archivo y <xref:Microsoft.VisualStudio.Utilities.IContentType> objetos.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|La colección de objetos <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|Objetos <xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Muchos de los objetos de adaptador de editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Un <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> objeto para obtener una vista de texto dado.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> de diferencias.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> de diferencias.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> o <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> para un conjunto de <xref:Microsoft.VisualStudio.Text.ITextBuffer> objetos.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantiene la colección de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objetos.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> para un búfer de texto.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> para obtener una vista de texto.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|El <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> para el ámbito especificado.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> para obtener una vista de texto.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtiene la sangría automática a través de la <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objetos.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Administra la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> para un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera texto con formato RTF a partir de un conjunto de intervalos de instantánea.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Un <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> para dar formato a líneas de texto en una vista.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> de objeto para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Busca una instantánea de texto.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> para un <xref:Microsoft.VisualStudio.Text.ITextBuffer> por <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> para obtener una vista de texto.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un conjunto estándar de glifos.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Realiza un seguimiento de teclado de control.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Estándar <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objetos.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relación entre búferes de texto y <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objetos.|  
  
## <a name="other-imports"></a>Otras importaciones  
 Los agentes y generadores de proveedores generalmente son entidades que pueden tener varias instancias en varios componentes.  
  
|Importar|Proporciona|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) para el búfer dado.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un etiquetador de marcador de texto (un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> para un determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)

