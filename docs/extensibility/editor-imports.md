---
title: Importaciones del editor | Microsoft Docs
description: Obtenga información acerca de cómo importar servicios, generadores y agentes de editor que proporcionan la extensión con distintos tipos de acceso al editor principal.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aef66be9797967b8c551ad4d1674c0b7be7aad81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883485"
---
# <a name="editor-imports"></a>Importaciones del editor
Puede importar un número de servicios, generadores y agentes de editor que proporcionen a la extensión distintos tipos de acceso al editor básico. Por ejemplo, puede importar <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> para proporcionar un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> para un tipo de contenido determinado. (Este navegador permite realizar diferentes tipos de búsquedas en un búfer de texto).

 Para usar una importación de editor, se importa como un campo o propiedad de una clase que exporta una Managed Extensibility Framework parte del componente.

> [!NOTE]
> Para obtener más información sobre el Managed Extensibility Framework, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Sintaxis de importación
 En el ejemplo siguiente se muestra cómo importar el servicio de generador de opciones del editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Si desea importar el servicio como un campo y no una propiedad, debe establecerlo `null` en en la declaración con el fin de evitar las advertencias del compilador sobre no asignar a una variable:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Para obtener más ejemplos de cómo usar las importaciones, vea los siguientes tutoriales:

- [Tutorial: crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Tutorial: personalizar la vista de texto](../extensibility/walkthrough-customizing-the-text-view.md)

- [Tutorial: resaltar texto](../extensibility/walkthrough-highlighting-text.md)

- [Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Tutorial: Mostrar ayuda para las firmas](../extensibility/walkthrough-displaying-signature-help.md)

- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)

- [Tutorial: Mostrar sugerencias de bombillas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importar el proveedor de servicios
 También puede importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (encontrado en el ensamblado Microsoft. VisualStudio. Shell. immutable. 10.0) de la misma manera para obtener acceso a los servicios de Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Vea [Tutorial: acceso al objeto DTE desde una extensión de editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) para obtener más información.

## <a name="services"></a>Servicios
 Los servicios de editor son generalmente entidades únicas que proporcionan un servicio y se comparten entre varios componentes.

|Importar|Muestra|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relación entre las extensiones de archivo y los <xref:Microsoft.VisualStudio.Utilities.IContentType> objetos.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|La colección de objetos <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> los.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Muchos objetos de adaptador de editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Objeto para una vista de texto determinada.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>De diferencias.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>De diferencias.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>O <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Para un conjunto de <xref:Microsoft.VisualStudio.Text.ITextBuffer> objetos.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Para un <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>Para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantiene la colección de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objetos.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Para un búfer de texto.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Para una vista de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Para el ámbito especificado.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>Para una vista de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>Para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtiene la sangría automática a través de los <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objetos.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Administra el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> para un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Una clase <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera texto con formato RTF a partir de un conjunto de intervalos de instantánea.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>Para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Para aplicar formato a las líneas de texto en una vista.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Objeto para <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Busca una instantánea de texto.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>Para un <xref:Microsoft.VisualStudio.Text.ITextBuffer> por <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>Para una vista de texto.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Conjunto estándar de glifos.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>Para un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Realiza el seguimiento del control del teclado.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Objetos estándar.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relación entre los búferes de texto y los  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objetos.|

## <a name="other-imports"></a>Otras importaciones
 Los generadores de proveedores y los agentes son generalmente entidades que pueden tener varias instancias en varios componentes.

|Importar|Muestra|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>De tipo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) para el búfer especificado.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un etiquetador de marcador de texto (una <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Para un determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Una clase <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Vea también
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
