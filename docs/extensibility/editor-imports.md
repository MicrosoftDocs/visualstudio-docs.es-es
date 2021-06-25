---
title: Editor Imports | Microsoft Docs
description: Obtenga información sobre cómo importar servicios de editor, generadores y agentes que proporcionan a la extensión diferentes tipos de acceso al editor principal.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898349"
---
# <a name="editor-imports"></a>Importaciones del editor
Puede importar una serie de servicios de editor, generadores y agentes que proporcionan a la extensión distintos tipos de acceso al editor principal. Por ejemplo, puede importar para <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> proporcionarle un para un tipo de contenido <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> determinado. (Este navegador permite realizar diferentes tipos de búsquedas en un búfer de texto).

 Para usar una importación del editor, se importa como un campo o propiedad de una clase que exporta un Managed Extensibility Framework componente.

> [!NOTE]
> Para obtener más información sobre la Managed Extensibility Framework, [vea Managed Extensibility Framework (MEF).](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>Sintaxis de importación
 En el ejemplo siguiente se muestra cómo importar el servicio de generador de opciones del editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Si desea importar el servicio como un campo y no como una propiedad, debe establecerlo en en la declaración para evitar las advertencias del compilador sobre no asignar `null` a una variable:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Para obtener más ejemplos del uso de importaciones, consulte los tutoriales siguientes:

- [Tutorial: Creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Tutorial: Personalización de la vista de texto](../extensibility/walkthrough-customizing-the-text-view.md)

- [Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md)

- [Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Tutorial: Mostrar la Ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)

- [Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importación del proveedor de servicios
 También puede importar un (que se encuentra en el ensamblado Microsoft.VisualStudio.Shell.Immutable.10.0) de la misma manera para obtener acceso a los servicios de <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Vea [Tutorial: Acceso al objeto DTE desde una extensión del editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) para obtener más información.

## <a name="services"></a>Servicios
 Los servicios del editor suelen ser entidades únicas que proporcionan un servicio y se comparten entre varios componentes.

|Importar|Proporciona|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relación entre las extensiones de archivo y los <xref:Microsoft.VisualStudio.Utilities.IContentType> objetos.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|La colección de objetos <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Objetos.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Muchos objetos de adaptador de editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Objeto <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> para una vista de texto determinada.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Una <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> de diferencias.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Una <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> de diferencias.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|o <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|para <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> un conjunto de objetos <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|para <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.ITextBuffer> un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|para <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|para <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|para <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantiene la colección de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objetos .|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|para <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> un búfer de texto.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|para <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> una vista de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|para <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> el ámbito especificado.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|para <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> una vista de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|para <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtiene la sangría automática a través de los <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objetos .|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Administra para <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> un .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera texto con formato RTF a partir de un conjunto de intervalos de instantáneas.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|para <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|para <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> dar formato a las líneas de texto de una vista.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Objeto <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un objeto .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Busca una instantánea de texto.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|para <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> un <xref:Microsoft.VisualStudio.Text.ITextBuffer> de <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|para <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> una vista de texto.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Conjunto estándar de glifos.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|para <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Realiza un seguimiento del control del teclado.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Objetos <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> estándar.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relación entre los búferes de texto y  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> los objetos.|

## <a name="other-imports"></a>Otras importaciones
 Los generadores de proveedores y los agentes suelen ser entidades que pueden tener varias instancias en varios componentes.

|Importar|Proporciona|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|de <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> tipo ) para el búfer <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> especificado.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Etiquetador de marcador de texto (de <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|para <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> un objeto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> determinado.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Consulta también
- [Puntos de extensión del editor y del servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
