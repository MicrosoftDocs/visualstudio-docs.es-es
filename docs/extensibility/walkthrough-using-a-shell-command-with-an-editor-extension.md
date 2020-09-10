---
title: Usar un comando de Shell con una extensión de editor
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ebec1b2c58f5a2ae79e6f361d74e57cd935c177
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742032"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Tutorial: usar un comando de Shell con una extensión de editor
Desde un VSPackage, puede agregar características como comandos de menú al editor. En este tutorial se muestra cómo agregar un elemento gráfico a una vista de texto en el editor invocando un comando de menú.

 En este tutorial se muestra el uso de un VSPackage junto con una parte del componente de Managed Extensibility Framework (MEF). Debe usar un VSPackage para registrar el comando de menú con el shell de Visual Studio. Además, puede usar el comando para tener acceso a la parte del componente MEF.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú
 Cree un VSPackage que coloque un comando de menú denominado **Agregar elemento gráfico** en el menú **herramientas** .

1. Cree un proyecto VSIX de C# denominado `MenuCommandTest` y agregue un nombre de plantilla de elemento de comando personalizado **AddAdornment**. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Se abre una solución denominada MenuCommandTest. El archivo MenuCommandTestPackage tiene el código que crea el comando de menú y lo coloca en el menú **herramientas** . En este momento, el comando solo hace que aparezca un cuadro de mensaje. En los pasos posteriores se mostrará cómo cambiar esto para mostrar el elemento gráfico de comentario.

3. Abra el archivo *source. Extension. vsixmanifest* en el editor de manifiestos de VSIX. La `Assets` pestaña debe tener una fila para un Microsoft. VisualStudio. VsPackage denominado MenuCommandTest.

4. Guarde y cierre el archivo *source. Extension. vsixmanifest* .

## <a name="add-a-mef-extension-to-the-command-extension"></a>Agregar una extensión MEF a la extensión de comando

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución, haga clic en **Agregar**y, a continuación, en **nuevo proyecto**. En el cuadro de diálogo **Agregar nuevo proyecto** , haga clic en **extensibilidad** en **Visual C#** y, a continuación, en **Proyecto VSIX**. Dé un nombre al proyecto `CommentAdornmentTest`.

2. Dado que este proyecto interactuará con el ensamblado VSPackage con nombre seguro, debe firmar el ensamblado. Puede volver a usar el archivo de clave ya creado para el ensamblado VSPackage.

    1. Abra las propiedades del proyecto y seleccione la pestaña **firma** .

    2. Seleccione **firmar el ensamblado**.

    3. En **elegir un archivo de clave de nombre seguro**, seleccione el archivo *key. snk* que se generó para el ensamblado MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Consulte la extensión de MEF en el proyecto VSPackage
 Dado que va a agregar un componente MEF al VSPackage, debe especificar ambos tipos de recursos en el manifiesto.

> [!NOTE]
> Para obtener más información sobre MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Para hacer referencia al componente MEF en el proyecto VSPackage

1. En el proyecto MenuCommandTest, abra el archivo *source. Extension. vsixmanifest* en el editor de manifiestos de VSIX.

2. En la pestaña **activos** , haga clic en **nuevo**.

3. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

4. En la lista **origen** , elija **un proyecto en la solución actual**.

5. En la lista **proyecto** , elija **CommentAdornmentTest**.

6. Guarde y cierre el archivo *source. Extension. vsixmanifest* .

7. Asegúrese de que el proyecto MenuCommandTest tiene una referencia al proyecto CommentAdornmentTest.

8. En el proyecto CommentAdornmentTest, establezca el proyecto para que genere un ensamblado. En el **Explorador de soluciones**, seleccione el proyecto y mire en la ventana **propiedades** para la propiedad copiar el resultado de la **compilación en OutputDirectory** y establézcalo en **true**.

## <a name="define-a-comment-adornment"></a>Definir un elemento gráfico de comentarios
 El elemento gráfico de comentario se compone de un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que realiza un seguimiento del texto seleccionado y de algunas cadenas que representan el autor y la descripción del texto.

#### <a name="to-define-a-comment-adornment"></a>Para definir un elemento gráfico de comentarios

1. En el proyecto CommentAdornmentTest, agregue un nuevo archivo de clase y asígnele el nombre `CommentAdornment` .

2. Agregue las siguientes referencias:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Agregue la siguiente `using` Directiva.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. El archivo debe contener una clase denominada `CommentAdornment` .

    ```csharp
    internal class CommentAdornment
    ```

5. Agregue tres campos a la `CommentAdornment` clase para <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , el autor y la descripción.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Agregue un constructor que inicialice los campos.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Crear un elemento visual para el elemento gráfico
 Defina un elemento visual para el elemento gráfico. Para este tutorial, defina un control que herede de la clase Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas> .

1. Cree una clase en el proyecto CommentAdornmentTest y asígnele el nombre `CommentBlock` .

2. Agregue las siguientes `using` directivas.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Haga que la `CommentBlock` clase herede de <xref:System.Windows.Controls.Canvas> .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Agregue algunos campos privados para definir los aspectos visuales del elemento gráfico.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Agregue un constructor que defina el elemento gráfico de comentarios y agregue el texto pertinente.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Implemente también un <xref:System.Windows.Controls.Panel.OnRender%2A> controlador de eventos que dibuje el elemento gráfico.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Agregar un IWpfTextViewCreationListener
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>Es una parte del componente de MEF que puede usar para escuchar los eventos de creación de la vista.

1. Agregue un archivo de clase al proyecto CommentAdornmentTest y asígnele el nombre `Connector` .

2. Agregue las siguientes `using` directivas.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Declare una clase que implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> y expórtelo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Text" y un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . El atributo Content Type Especifica el tipo de contenido al que se aplica el componente. El tipo de texto es el tipo base para todos los tipos de archivo no binarios. Por consiguiente, casi todas las vistas de texto que se crean serán de este tipo. El atributo role de la vista de texto especifica el tipo de vista de texto a la que se aplica el componente. Los roles de la vista de texto del documento suelen mostrar texto compuesto por líneas y se almacena en un archivo.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que llame al `Create()` evento estático de `CommentAdornmentManager` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Agregue un método que puede usar para ejecutar el comando.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Definir una capa de elementos gráficos
 Para agregar un elemento gráfico nuevo, debe definir una capa de elemento gráfico.

### <a name="to-define-an-adornment-layer"></a>Para definir una capa de elementos gráficos

1. En la `Connector` clase, declare un campo público de tipo <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> y expórtelo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> que especifique un nombre único para la capa de elementos gráficos y un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> que defina la relación de orden Z de esta capa de gráfico con las demás capas de la vista de texto (texto, símbolo de intercalación y selección).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Proporcionar elementos gráficos de comentarios
 Al definir un elemento gráfico, implemente también un proveedor de elementos gráficos de comentarios y un administrador de adornos de comentarios. El proveedor de adornos de comentario mantiene una lista de elementos gráficos de comentarios, escucha <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> los eventos en el búfer de texto subyacente y elimina los elementos gráficos de comentario cuando se elimina el texto subyacente.

1. Agregue un nuevo archivo de clase al proyecto CommentAdornmentTest y asígnele el nombre `CommentAdornmentProvider` .

2. Agregue las siguientes `using` directivas.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Agregue una clase denominada `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Agregue campos privados para el búfer de texto y la lista de elementos gráficos de comentarios relacionados con el búfer.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Agregue un constructor para `CommentAdornmentProvider` . Este constructor debe tener acceso privado porque el método crea instancias del proveedor `Create()` . El constructor agrega el `OnBufferChanged` controlador de eventos al <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Agregue el método `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Agregue el método `Detach()`.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Agregue el `OnBufferChanged` controlador de eventos.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Agregue una declaración para un `CommentsChanged` evento.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Cree un `Add()` método para agregar el elemento gráfico.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Agregue un `RemoveComments()` método.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Agregue un `GetComments()` método que devuelva todos los comentarios en un intervalo de instantánea determinado.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Agregue una clase denominada `CommentsChangedEventArgs` , como se indica a continuación.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Administrar elementos gráficos de comentarios
 El administrador de adornos de comentario crea el elemento gráfico y lo agrega a la capa de elemento gráfico. Escucha los <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> eventos y para <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> que pueda moverse o eliminar el elemento gráfico. También escucha el `CommentsChanged` evento desencadenado por el proveedor de elementos gráficos de comentarios cuando se agregan o quitan Comentarios.

1. Agregue un archivo de clase al proyecto CommentAdornmentTest y asígnele el nombre `CommentAdornmentManager` .

2. Agregue las siguientes `using` directivas.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Agregue una clase denominada `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Agregue algunos campos privados.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Agregue un constructor que suscriba el administrador a los <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> eventos y <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> , y también al `CommentsChanged` evento. El constructor es privado porque el método estático crea instancias del administrador `Create()` .

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Agregue el `Create()` método que obtiene un proveedor o crea uno si es necesario.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Agregue el `CommentsChanged` controlador.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Agregue el <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> controlador.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Agregue el <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> controlador.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Agregue el método privado que dibuja el comentario.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Usar el comando de menú para agregar el elemento gráfico de comentarios
 Puede usar el comando de menú para crear un elemento gráfico de comentario implementando el `MenuItemCallback` método del VSPackage.

1. Agregue las siguientes referencias al proyecto MenuCommandTest:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. Text. UI. WPF

2. Abra el archivo *AddAdornment.CS* y agregue las siguientes `using` directivas.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Elimine el `Execute()` método y agregue el siguiente controlador de comandos.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Agregue código para obtener la vista activa. Debe obtener el `SVsTextManager` de Visual Studio Shell para obtener el activo `IVsTextView` .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Si esta vista de texto es una instancia de una vista de texto del editor, puede convertirla en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> interfaz y, a continuación, obtener el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> y su asociado <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Use <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> para llamar al `Connector.Execute()` método, que obtiene el proveedor del elemento gráfico de comentarios y agrega el elemento gráfico. El controlador de comandos debería tener ahora el siguiente aspecto:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Establezca el método AddAdornmentHandler como el controlador para el comando AddAdornment en el constructor AddAdornment.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Compilar y probar el código

1. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

2. Crear un archivo de texto Escriba algo de texto y, a continuación, selecciónelo.

3. En el menú **herramientas** , haga clic en **invocar Agregar elemento gráfico**. Un globo debe aparecer en el lado derecho de la ventana de texto y debe contener texto similar al texto siguiente.

     SuNombreDeUsuario

     Fourscore...

## <a name="see-also"></a>Vea también
- [Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
