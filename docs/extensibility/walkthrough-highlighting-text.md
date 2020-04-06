---
title: 'Tutorial: Resaltar texto ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697399"
---
# <a name="walkthrough-highlight-text"></a>Tutorial: Resaltar texto
Puede agregar diferentes efectos visuales al editor mediante la creación de componentes de Managed Extensibility Framework (MEF). En este tutorial se muestra cómo resaltar cada aparición de la palabra actual en un archivo de texto. Si una palabra se produce más de una vez en un archivo de texto y coloca el intercalador en una ocurrencia, se resalta cada aparición.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `HighlightWordTest`nombre a la solución .

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

## <a name="define-a-textmarkertag"></a>Definir un TextMarkerTag
 El primer paso para resaltar texto <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> es subclase y definir su apariencia.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Para definir un TextMarkerTag y un MarkerFormatDefinition

1. Agregue un archivo de clase y asímócle el nombre **HighlightWordTag**.

2. Agregue las siguientes referencias:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentation.Core

    8. Presentation.Framework

3. Importe los siguientes espacios de nombres.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Cree una clase que <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> herede `HighlightWordTag`de ella y asíánte .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Cree una segunda clase <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>que herede `HighlightWordFormatDefinition`de , y asímóquela. Para utilizar esta definición de formato para la etiqueta, debe exportarla con los siguientes atributos:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: las etiquetas lo utilizan para hacer referencia a este formato

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: esto hace que el formato aparezca en la interfaz de usuario

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. En el constructor de HighlightWordFormatDefinition, defina su nombre para mostrar y apariencia. La propiedad Background define el color de relleno, mientras que la propiedad Foreground define el color del borde.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. En el constructor de HighlightWordTag, pase el nombre de la definición de formato que ha creado.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementar un ITagger
 El siguiente paso es <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementar la interfaz. Esta interfaz asigna, a un búfer de texto determinado, etiquetas que proporcionan resaltado de texto y otros efectos visuales.

### <a name="to-implement-a-tagger"></a>Para implementar un tagger

1. Cree una clase <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> que `HighlightWordTag`implemente de `HighlightWordTagger`tipo y asímismo.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Agregue los siguientes campos y propiedades privados a la clase:

    - Un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, que corresponde a la vista de texto actual.

    - Un <xref:Microsoft.VisualStudio.Text.ITextBuffer>, que corresponde al búfer de texto que subyace a la vista de texto.

    - Un <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, que se utiliza para buscar texto.

    - Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, que tiene métodos para navegar dentro de intervalos de texto.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, que contiene el conjunto de palabras que se resaltará.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, que corresponde a la palabra actual.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, que corresponde a la posición actual del intercalador.

    - Un objeto de bloqueo.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Agregue un constructor que inicialice las propiedades <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> enumeradas anteriormente y agregue y controladores de eventos.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Los controladores de `UpdateAtCaretPosition` eventos llaman al método.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. También debe agregar `TagsChanged` un evento al que llama el método update.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. El `UpdateAtCaretPosition()` método busca cada palabra en el búfer de texto que es idéntica a <xref:Microsoft.VisualStudio.Text.SnapshotSpan> la palabra donde se coloca el cursor y construye una lista de objetos que corresponden a las apariciones de la palabra. A continuación, llama `SynchronousUpdate`a `TagsChanged` , que genera el evento.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. El `SynchronousUpdate` realiza una actualización `WordSpans` sincrónica en el y `CurrentWord` propiedades y provoca el `TagsChanged` evento.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Debe implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> el método. Este método toma <xref:Microsoft.VisualStudio.Text.SnapshotSpan> una colección de objetos y devuelve una enumeración de intervalos de etiquetas.

     Implemente este método como un iterador de rendimiento, que permite la evaluación diferida (es decir, la evaluación del conjunto solo cuando se tiene acceso a elementos individuales) de las etiquetas. En Visual Basic, agregue las etiquetas a una lista y devuelva la lista.

     Aquí el método <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> devuelve un objeto <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>que tiene un "azul", que proporciona un fondo azul.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Crear un proveedor de Tagger
 Para crear el etiquetador, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>debe implementar un archivo . Esta clase es una parte del componente MEF, por lo que debe establecer los atributos correctos para que se reconozca esta extensión.

> [!NOTE]
> Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Para crear un proveedor de etiquetas

1. Cree una `HighlightWordTaggerProvider` clase denominada <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>que implemente y <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> expórtela <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>con un de "texto" y un archivo .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Debe importar dos servicios <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> de <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>editor, el y el , para crear instancias del etiquetador.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> el método para `HighlightWordTagger`devolver una instancia de .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Compile y pruebe el código
 Para probar este código, compile la solución HighlightWordTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Para compilar y probar la solución HighlightWordTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto en el que se repitan las palabras, por ejemplo, "hola hola hola".

4. Coloque el cursor en una de las apariciones de "hola". Cada ocurrencia debe resaltarse en azul.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
