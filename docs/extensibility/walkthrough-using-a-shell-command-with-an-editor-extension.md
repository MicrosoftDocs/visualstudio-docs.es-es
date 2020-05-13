---
title: 'Tutorial: Uso de un comando de Shell con una extensión de editor . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697161"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Tutorial: Utilice un comando shell con una extensión de editor
Desde un VSPackage, puede agregar características como comandos de menú al editor. En este tutorial se muestra cómo agregar un adorno a una vista de texto en el editor invocando un comando de menú.

 En este tutorial se muestra el uso de un VSPackage junto con un componente de Managed Extensibility Framework (MEF). Debe usar un VSPackage para registrar el comando de menú con el shell de Visual Studio. Además, puede utilizar el comando para acceder a la parte del componente MEF.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú
 Crear un VSPackage que coloca un comando de menú denominado **Agregar adornación** en el **herramientas** menú.

1. Cree un proyecto vSIX `MenuCommandTest`de C- con el nombre y agregue un nombre de plantilla de elemento de comando personalizado **AddAdornment**. Para obtener más información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Se abre una solución denominada MenuCommandTest. El MenuCommandTestPackage archivo tiene el código que crea el comando de menú y lo coloca en el **herramientas** menú. En este punto, el comando solo hace que aparezca un cuadro de mensaje. Los pasos posteriores mostrarán cómo cambiar esto para mostrar el adorno del comentario.

3. Abra el archivo *source.extension.vsixmanifest* en el Editor de manifiestos de VSIX. La `Assets` pestaña debe tener una fila para un Microsoft.VisualStudio.VsPackage denominado MenuCommandTest.

4. Guarde y cierre el archivo *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Agregue una extensión MEF a la extensión de comando

1. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo de solución, haga clic en **Agregar**y, a continuación, haga clic en **Nuevo proyecto**. En el cuadro de diálogo **Agregar nuevo proyecto** , **VSIX Project**haga clic en **Extensibilidad** en Visual **C .** Asigne el nombre al proyecto `CommentAdornmentTest`.

2. Dado que este proyecto interactuará con el ensamblado VSPackage con nombre seguro, debe firmar el ensamblado. Puede reutilizar el archivo de clave ya creado para el ensamblado VSPackage.

    1. Abra las propiedades del proyecto y seleccione la pestaña **Firma.**

    2. Seleccione **Firmar el ensamblado**.

    3. En **Elegir un archivo**de clave de nombre seguro , seleccione el archivo *Key.snk* que se generó para el ensamblado MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Consulte la extensión MEF en el proyecto VSPackage
 Dado que va a agregar un componente MEF al VSPackage, debe especificar ambos tipos de activos en el manifiesto.

> [!NOTE]
> Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Para hacer referencia al componente MEF en el proyecto VSPackage

1. En el proyecto MenuCommandTest, abra el archivo *source.extension.vsixmanifest* en el Editor de manifiestos VSIX.

2. En la pestaña **Activos,** haga clic en **Nuevo**.

3. En la lista **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.

4. En la lista **Origen,** elija Un proyecto en la **solución actual.**

5. En la lista **Proyecto** , elija **CommentAdornmentTest**.

6. Guarde y cierre el archivo *source.extension.vsixmanifest.*

7. Asegúrese de que el MenuCommandTest proyecto tiene una referencia a la CommentAdornmentTest proyecto.

8. En el proyecto CommentAdornmentTest, establezca el proyecto para generar un ensamblado. En el **Explorador**de soluciones , seleccione el proyecto y busque en la ventana **Propiedades** de la propiedad **Copiar salida de compilación en OutputDirectory** y establézcalo en **true**.

## <a name="define-a-comment-adornment"></a>Definir un adorno de comentario
 El propio adorno de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> comentario consta de un que realiza un seguimiento del texto seleccionado y algunas cadenas que representan al autor y la descripción del texto.

#### <a name="to-define-a-comment-adornment"></a>Para definir un adorno de comentario

1. En el proyecto CommentAdornmentTest, agregue un `CommentAdornment`nuevo archivo de clase y asímóquele.

2. Agregue las siguientes referencias:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Agregue la `using` siguiente directiva.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. El archivo debe contener `CommentAdornment`una clase denominada .

    ```csharp
    internal class CommentAdornment
    ```

5. Agregue tres campos `CommentAdornment` a <xref:Microsoft.VisualStudio.Text.ITrackingSpan>la clase para el , el autor y la descripción.

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

## <a name="create-a-visual-element-for-the-adornment"></a>Cree un elemento visual para el adorno
 Defina un elemento visual para el adorno. Para este tutorial, defina un control que herede de <xref:System.Windows.Controls.Canvas>la clase Windows Presentation Foundation (WPF).

1. Cree una clase en el proyecto CommentAdornmentTest y `CommentBlock`asío.

2. Agregue las `using` siguientes directivas.

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

3. Haga `CommentBlock` que la <xref:System.Windows.Controls.Canvas>clase herede de .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Agregue algunos campos privados para definir los aspectos visuales del adorno.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Agregue un constructor que defina el adorno de comentarioy agregue el texto relevante.

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

6. Implemente también <xref:System.Windows.Controls.Panel.OnRender%2A> un controlador de eventos que dibuje el adorno.

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
 Es <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> una parte del componente MEF que puede utilizar para escuchar eventos de creación.

1. Agregue un archivo de clase al proyecto `Connector`CommentAdornmentTest y asímócle el nombre .

2. Agregue las `using` siguientes directivas.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Declare una clase <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>que implemente y <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> expórtela <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> con <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>un de "texto" y un archivo de archivo . El atributo de tipo de contenido especifica el tipo de contenido al que se aplica el componente. El tipo de texto es el tipo base para todos los tipos de archivo no binarios. Por lo tanto, casi todas las vistas de texto que se crean serán de este tipo. El atributo de rol de vista de texto especifica el tipo de vista de texto a la que se aplica el componente. Los roles de vista de texto de documento generalmente muestran texto que se compone de líneas y se almacena en un archivo.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> el método para que `Create()` llame `CommentAdornmentManager`al evento estático del archivo .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Agregue un método que pueda utilizar para ejecutar el comando.

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

## <a name="define-an-adornment-layer"></a>Definir una capa de adorno
 Para agregar un nuevo adorno, debe definir una capa de adorno.

### <a name="to-define-an-adornment-layer"></a>Para definir una capa de adorno

1. En `Connector` la clase, declare un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>campo público de <xref:Microsoft.VisualStudio.Utilities.NameAttribute> tipo y expórtelo con <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> un que especifique un nombre único para la capa de adorno y un que defina la relación de orden Z de esta capa de adorno con las otras capas de vista de texto (texto, intercalador y selección).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Proporcionar adornos de comentarios
 Al definir un adorno, también implemente un proveedor de adornos de comentarios y un administrador de adornos de comentarios. El proveedor de adornos de comentarios mantiene una <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> lista de adornos de comentarios, escucha eventos en el búfer de texto subyacente y elimina los adornos de comentarios cuando se elimina el texto subyacente.

1. Agregue un nuevo archivo de clase al proyecto `CommentAdornmentProvider`CommentAdornmentTest y asímócle el nombre .

2. Agregue las `using` siguientes directivas.

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

4. Agregue campos privados para el búfer de texto y la lista de adornos de comentarios relacionados con el búfer.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Agregue un `CommentAdornmentProvider`constructor para . Este constructor debe tener acceso privado porque `Create()` el método crea una instancia del proveedor. El constructor agrega `OnBufferChanged` el controlador <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> de eventos al evento.

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

8. Agregue `OnBufferChanged` el controlador de eventos.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Agregue una declaración para un `CommentsChanged` evento.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Cree `Add()` un método para agregar el adorno.

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

11. Agregue `RemoveComments()` un método.

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

12. Agregue `GetComments()` un método que devuelva todos los comentarios de un intervalo de instantáneas determinado.

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

13. Agregue una `CommentsChangedEventArgs`clase denominada , como se indica a continuación.

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

## <a name="manage-comment-adornments"></a>Gestionar adornos de comentarios
 El administrador de adornos de comentarios crea el adorno y lo agrega a la capa de adorno. Escucha los <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> eventos <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> y para que pueda mover o eliminar el adorno. También escucha el `CommentsChanged` evento que desencadena el proveedor de adornos de comentarios cuando se agregan o quitan comentarios.

1. Agregue un archivo de clase al proyecto `CommentAdornmentManager`CommentAdornmentTest y asímócle el nombre .

2. Agregue las `using` siguientes directivas.

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

5. Agregue un constructor que suscribe <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> el administrador a `CommentsChanged` los eventos y, así como al evento. El constructor es privado porque el método `Create()` estático crea una instancia del administrador.

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

6. Agregue `Create()` el método que obtiene un proveedor o crea uno si es necesario.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Agregue `CommentsChanged` el controlador.

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

8. Agregue <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> el controlador.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Agregue <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> el controlador.

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

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Utilice el comando de menú para agregar el adorno de comentario
 Puede usar el comando de menú para crear `MenuItemCallback` un adorno de comentario mediante la implementación del método de la VSPackage.

1. Agregue las siguientes referencias al proyecto MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Abra el archivo *AddAdornment.cs* `using` y agregue las siguientes directivas.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Elimine `Execute()` el método y agregue el siguiente controlador de comandos.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Agregue código para obtener la vista activa. Debe obtener `SVsTextManager` el shell de Visual Studio `IVsTextView`para obtener el archivo .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Si esta vista de texto es una instancia de una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> vista de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> texto del <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>editor, puede convertirla en la interfaz y, a continuación, obtener el archivo . Utilice <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> el para `Connector.Execute()` llamar al método, que obtiene el proveedor de adorno de comentarioy agrega el adorno. El controlador de comandos ahora debería parecerse a este código:

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

6. Establecer el AddAdornmentHandler método como el controlador para el AddAdornment comando en el AddAdornment constructor.

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

## <a name="build-and-test-the-code"></a>Compile y pruebe el código

1. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

2. Crear un archivo de texto Escriba algo de texto y, a continuación, selecciónelo.

3. En el menú **Herramientas** , haga clic en **Invocar agregar adorno**. Un globo debe mostrarse en el lado derecho de la ventana de texto y debe contener texto similar al texto siguiente.

     YourUserName

     Ochenta...

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
