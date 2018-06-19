---
title: Editor de importaciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f01567efa411187bede4f6daf15012da81c2331f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132739"
---
# <a name="editor-imports"></a>Editor de importaciones
Puede importar un número de servicios de editor, generadores y agentes que proporcionan la extensión con distintos tipos de acceso al editor principal. Por ejemplo, puede importar el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> para proporcionarle una <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> para un tipo de contenido determinado. (Este navegador permite que realizar diferentes tipos de búsquedas en un búfer de texto).  
  
 Para usar una importación de editor, importa como un campo o propiedad de una clase que se exporta una parte del componente de Managed Extensibility Framework.  
  
> [!NOTE]
>  Para obtener más información acerca de Managed Extensibility Framework, consulte [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
## <a name="import-syntax"></a>Sintaxis de importación  
 En el ejemplo siguiente se muestra cómo importar el editor de servicio de factoría de opciones.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Si desea importar el servicio como un campo y no una propiedad, debe establecer en `null` en la declaración con el fin de evitar las advertencias del compilador sobre no se asigna a una variable:  
  
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
  
 [Tutorial: visualización de sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## <a name="importing-the-service-provider"></a>Importar el proveedor de servicios  
 También puede importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (que se encuentra en el ensamblado Microsoft.VisualStudio.Shell.Immutable.10.0) de la misma manera para obtener acceso a los servicios de Visual Studio:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Vea [Tutorial: obtener acceso a los del objeto DTE desde una extensión del Editor de](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) para obtener más información.  
  
## <a name="services"></a>Servicios  
 Editor de servicios es entidades generalmente únicas que proporcionan un servicio y se comparten entre varios componentes.  
  
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
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Un <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> para dar formato a las líneas de texto en una vista.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> de objeto para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Busca en una instantánea de texto.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> para un <xref:Microsoft.VisualStudio.Text.ITextBuffer> por <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> para obtener una vista de texto.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un conjunto estándar de glifos.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Realiza un seguimiento de teclado de control.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Estándar <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objetos.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relación entre búferes de texto y <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objetos.|  
  
## <a name="other-imports"></a>Otras importaciones  
 Agentes y generadores de proveedores generalmente son entidades que pueden tener varias instancias en varios componentes.  
  
|Importar|Proporciona|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) para el búfer dado.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un etiquetador de marcador de texto (un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> para un determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)