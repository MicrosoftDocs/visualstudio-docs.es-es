---
title: Importaciones de Editores (Editor Imports) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712011"
---
# <a name="editor-imports"></a>Importaciones de editores
Puede importar una serie de servicios de editor, fábricas y intermediarios que proporcionan a su extensión diferentes tipos de acceso al editor principal. Por ejemplo, puede <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> importar el para <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> proporcionarle un para un tipo de contenido determinado. (Este navegador le permite realizar diferentes tipos de búsquedas en un búfer de texto.)

 Para usar una importación de editor, impórtela como un campo o propiedad de una clase que exporta un componente de Managed Extensibility Framework.

> [!NOTE]
> Para obtener más información acerca de Managed Extensibility Framework, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Sintaxis de importación
 En el ejemplo siguiente se muestra cómo importar el servicio de fábrica de opciones del editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Si desea importar el servicio como un campo y no `null` como una propiedad, debe establecerlo en la declaración para evitar las advertencias del compilador sobre no asignar a una variable:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Para obtener más ejemplos de uso de importaciones, consulte los siguientes tutoriales:

- [Tutorial: Crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Tutorial: Personalizar la vista de texto](../extensibility/walkthrough-customizing-the-text-view.md)

- [Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md)

- [Tutorial: Mostrar información sobre herramientas quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Tutorial: Mostrar la Ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)

- [Tutorial: Mostrar sugerencias de bombillas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importar el proveedor de servicios
 También puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> un (que se encuentra en el ensamblado Microsoft.VisualStudio.Shell.Immutable.10.0) de la misma manera para obtener acceso a los servicios de Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Consulte [Tutorial: Acceda al objeto DTE desde una extensión](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) de editor para obtener más información.

## <a name="services"></a>Servicios
 Los servicios de editor son generalmente entidades únicas que proporcionan un servicio y se comparten entre varios componentes.

|Importar|Proporciona|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relación entre <xref:Microsoft.VisualStudio.Utilities.IContentType> las extensiones de archivo y los objetos.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|La colección de objetos <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Objetos.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Muchos objetos de adaptador de editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Un <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> objeto para una vista de texto determinada.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Un valor de tipo <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Un valor de tipo <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Una <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> de las diferencias.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Una <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> de las diferencias.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> o <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>un archivo .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> para un <xref:Microsoft.VisualStudio.Text.ITextBuffer> conjunto de objetos.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> for <xref:Microsoft.VisualStudio.Text.ITextBuffer>a .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> for <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> for <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> for <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantiene la colección de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objetos.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> para un búfer de texto.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> para una vista de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|El <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> para el ámbito especificado.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> para una vista de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> for <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtiene la sangría automática <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> a través de los objetos.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Administra <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>for a .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Un valor de tipo <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera texto con formato RTF a partir de un conjunto de intervalos de instantáneas.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> for <xref:Microsoft.VisualStudio.Text.Editor.ITextView>an .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> para dar formato a las líneas de texto en una vista.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> objeto <xref:Microsoft.VisualStudio.Text.Editor.ITextView>para un archivo .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Busca una instantánea de texto.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> for <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>an by .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> para una vista de texto.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un conjunto estándar de glifos.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> for <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Realiza un seguimiento del manejo del teclado.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Objetos estándar. <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relación entre los <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> búferes de texto y los objetos.|

## <a name="other-imports"></a>Otras importaciones
 Las fábricas y los intermediarios de proveedores son generalmente entidades que pueden tener varias instancias en varios componentes.

|Importar|Proporciona|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>tipo ) para el búfer especificado.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un marcador de texto <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> (a de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un determinado .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Un valor de tipo <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Un valor de tipo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Un valor de tipo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Vea también
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
