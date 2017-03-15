---
title: 'Tutorial: Resaltar texto | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 029cc7785c49a08c7128bfaaff8f236e438efad8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-highlighting-text"></a>Tutorial: Resaltar texto
Puede agregar distintos efectos visuales en el editor mediante la creación de componentes de Managed Extensibility Framework (MEF). Este tutorial muestra cómo resaltar todas las apariciones de la palabra actual en un archivo de texto. Si una palabra aparece más de una vez en un archivo de texto y coloca el símbolo de intercalación de una ocurrencia, se resaltan todas las apariciones.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Crear un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) El nombre de la solución `HighlightWordTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="defining-a-textmarkertag"></a>Definir un TextMarkerTag  
 El primer paso para resaltar texto es subclase <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>y definir su apariencia.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Para definir un TextMarkerTag y un MarkerFormatDefinition  
  
1.  Agregue un archivo de clase y asígnele el nombre **HighlightWordTag**.  
  
2.  Agregue las siguientes referencias:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Importe los siguientes espacios de nombres.  
  
    ```c#  
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
  
4.  Cree una clase que hereda de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>y asígnele el nombre `HighlightWordTag`.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
    ```c#  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Cree una segunda clase que hereda de <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>y asígnele el nombre HighlightWordFormatDefinition.</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Para usar esta definición de formato de la etiqueta, debe exportarlo con los siguientes atributos:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: etiquetas utilizan para hacer referencia a este formato</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Esto hace que el formato que aparecen en la interfaz de usuario</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
    ```c#  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  En el constructor para HighlightWordFormatDefinition, defina su apariencia y nombre para mostrar. La propiedad Background define el color de relleno, mientras que la propiedad Foreground define el color del borde.  
  
    ```c#  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  En el constructor para HighlightWordTag, pase el nombre de la definición de formato que acaba de crear.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Implementar un ITagger  
 El siguiente paso es implementar la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>interfaz.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Esta interfaz se le asigna un búfer de texto dado, etiquetas que proporcionan el resaltado de texto y otros efectos visuales.  
  
#### <a name="to-implement-a-tagger"></a>Para implementar un etiquetador  
  
1.  Cree una clase que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>de tipo `HighlightWordTag`y asígnele el nombre `HighlightWordTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
    ```c#  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Agregue los siguientes campos privados y propiedades a la clase:  
  
    -   Un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, que corresponde a la vista de texto actual.</xref:Microsoft.VisualStudio.Text.Editor.ITextView>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.ITextBuffer>, que se corresponde con el búfer de texto subyacente a la vista de texto.</xref:Microsoft.VisualStudio.Text.ITextBuffer>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, que se usa para buscar texto.</xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, que tiene métodos para navegar dentro de intervalos de texto.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, que contiene el conjunto de palabras para resaltar.</xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, que corresponde a la palabra actual.</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, que corresponde a la posición actual del símbolo de intercalación.</xref:Microsoft.VisualStudio.Text.SnapshotPoint>  
  
    -   Un objeto de bloqueo.  
  
    ```c#  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  Agregue un constructor que inicializa las propiedades enumeradas anteriormente y agrega <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>y <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>controladores de eventos.</xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
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
  
4.  Los controladores de eventos que llaman a la `UpdateAtCaretPosition` (método).  
  
    ```c#  
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
  
5.  También debe agregar una `TagsChanged` eventos que se llama al método update.  
  
     [!code-cs[VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs) ] 
     [!code-vb [VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  El `UpdateAtCaretPosition()` método encuentra cada palabra en el búfer de texto que es idéntico a la palabra donde está situado el cursor y la crea una lista de <xref:Microsoft.VisualStudio.Text.SnapshotSpan>objetos que corresponden a las repeticiones de la palabra.</xref:Microsoft.VisualStudio.Text.SnapshotSpan> A continuación, se llama `SynchronousUpdate`, que genera el `TagsChanged` eventos.  
  
    ```c#  
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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  El `SynchronousUpdate` realiza una actualización sincrónica en el `WordSpans` y `CurrentWord` propiedades y genera el `TagsChanged` eventos.  
  
    ```vb  
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
  
8.  Debe implementar la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>método.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Este método toma una colección de <xref:Microsoft.VisualStudio.Text.SnapshotSpan>objetos y devuelve una enumeración de intervalos de etiqueta.</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
     En C#, implemente este método como un iterador yield, lo que permite la evaluación diferida (es decir, la evaluación del conjunto sólo cuando se tiene acceso a elementos individuales) de las etiquetas. En Visual Basic, agregue las etiquetas a una lista y devolver la lista.  
  
     Aquí, el método devuelve un <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>objeto que tiene un "blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, que proporciona un fondo azul.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>  
  
    ```c#  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>Crear un proveedor de etiquetador  
 Para crear el etiquetador, debe implementar un <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> Esta clase es un componente MEF, por lo que debe establecer los atributos correctos para que reconozca esta extensión.  
  
> [!NOTE]
>  Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>Para crear un proveedor de etiquetador  
  
1.  Cree una clase denominada `HighlightWordTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text" y una <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>  
  
    ```c#  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  Debe importar dos servicios de editor, el <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>y <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, para crear una instancia el etiquetador.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> </xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    ```c#  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>método para devolver una instancia de `HighlightWordTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>  
  
    ```c#  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución HighlightWordTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Para compilar y probar la solución HighlightWordTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto en el que se repiten las palabras, por ejemplo, "Hola Hola Hola".  
  
4.  Coloque el cursor en una de las apariciones de "hello". Todas las apariciones deben aparecer resaltada en azul.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
