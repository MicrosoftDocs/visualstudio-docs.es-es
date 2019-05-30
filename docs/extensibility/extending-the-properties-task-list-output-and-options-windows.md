---
title: Ampliar la salida de propiedades, la lista de tareas, las ventanas de opciones
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5186d7c16f89201b43ebabc49215c0afff4bbfd4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337116"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Extender las ventanas Propiedades, lista de tareas, resultados y opciones
Puede tener acceso a cualquier ventana de herramientas en Visual Studio. En este tutorial se muestra cómo integrar información acerca de la ventana de herramientas en un nuevo **opciones** página y una nueva configuración en el **propiedades** página y también cómo se escriben en el **delistadetareas** y **salida** windows.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Crear una extensión con una ventana de herramientas

1. Cree un proyecto denominado **TodoList** con la plantilla VSIX y agrega una plantilla de elemento de ventana de herramienta personalizada denominada **TodoWindow**.

    > [!NOTE]
    > Para obtener más información acerca de cómo crear una extensión con una ventana de herramientas, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Configuración de la ventana de herramientas
 Agregue un cuadro de texto que se va a escribir un nuevo elemento de lista de tareas, un botón para agregar el nuevo elemento a la lista y un cuadro de lista para mostrar los elementos en la lista.

1. En *TodoWindow.xaml*, eliminar los controles de botón, cuadro de texto y StackPanel de UserControl.

    > [!NOTE]
    > Esto no elimina el **button1_Click** controlador de eventos, que volverá a usar en un paso posterior.

2. Desde el **todos los controles de WPF** sección de la **cuadro de herramientas**, arrastre un **lienzo** control a la cuadrícula.

3. Arrastre un **TextBox**, un **botón**y un **ListBox** al lienzo. Organice los elementos para que el cuadro de texto y el botón se encuentran en el mismo nivel y el resto de la ventana por debajo de ellas, como se muestra en la siguiente imagen rellena el cuadro de lista.

     ![Finalizó la ventana de herramientas](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")

4. En el panel XAML, busque el botón y establezca su propiedad de contenido en **agregar**. Volver a conectar el controlador de eventos de botón para el control de botón agregando un `Click="button1_Click"` atributo. El bloque de lienzo debería tener este aspecto:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personalizar el constructor

1. En el *TodoWindowControl.xaml.cs* , agregue la siguiente instrucción using:

    ```csharp
    using System;
    ```

2. Agregue una referencia a la TodoWindow pública y tiene el constructor TodoWindowControl toman un parámetro TodoWindow. El código debe tener este aspecto:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. En *TodoWindow.cs*, cambie el constructor TodoWindowControl para incluir el parámetro TodoWindow. El código debe tener este aspecto:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Crear una página de opciones
 Puede proporcionar una página en el **opciones** cuadro de diálogo para que los usuarios pueden cambiar la configuración de la ventana de herramientas. Creación de una página de opciones requiere una clase que describe las opciones y una entrada en el *TodoListPackage.cs* o *TodoListPackage.vb* archivo.

1. Agregue una clase denominada `ToolsOptions.cs`. Realizar el `ToolsOptions` heredar clase <xref:Microsoft.VisualStudio.Shell.DialogPage>.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Agregue la siguiente instrucción using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. La página de opciones en este tutorial proporciona sólo una opción llamada DaysAhead. Agregar un campo privado denominado **daysAhead** y una propiedad denominada **DaysAhead** a la `ToolsOptions` clase:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Ahora debe convertir el proyecto conscientes de esta página de opciones.

### <a name="make-the-options-page-available-to-users"></a>Que la página de opciones disponibles para los usuarios

1. En *TodoWindowPackage.cs*, agregue un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la `TodoWindowPackage` clase:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. El primer parámetro al constructor ProvideOptionPage es el tipo de la clase `ToolsOptions`, que creó anteriormente. El segundo parámetro, "ToDo", es el nombre de la categoría en la **opciones** cuadro de diálogo. El tercer parámetro, "General", es el nombre de la subcategoría de la **opciones** donde estará disponible la página de opciones de cuadro de diálogo. Los dos parámetros siguientes son identificadores de recursos para las cadenas; el primero es el nombre de la categoría y el segundo es el nombre de la subcategoría. El último parámetro determina si se puede obtener acceso a esta página, utilizando la automatización.

     Cuando un usuario abre la página de opciones, debe ser similar a la siguiente imagen.

     ![Página de opciones](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Tenga en cuenta la categoría **ToDo** y la subcategoría **General**.

## <a name="make-data-available-to-the-properties-window"></a>Ponen a disposición de la ventana Propiedades
 Puede hacer disponible información de la lista de tareas mediante la creación de una clase denominada `TodoItem` que almacena información sobre los elementos individuales en la lista de tareas.

1. Agregue una clase denominada `TodoItem.cs`.

     Cuando la ventana de herramientas está disponible para los usuarios, los elementos en el cuadro de lista se representará mediante TodoItems. Cuando el usuario selecciona uno de estos elementos en el cuadro de lista, el **propiedades** ventana mostrará información sobre el elemento.

     Para que los datos estén disponibles en el **propiedades** ventana, convertir los datos en las propiedades públicas que tienen dos atributos especiales, `Description` y `Category`. `Description` es el texto que aparece en la parte inferior de la **propiedades** ventana. `Category` determina dónde debe aparecer la propiedad cuando la **propiedades** ventana se muestra en el **por categorías** vista. En la siguiente imagen, el **propiedades** ventana está en **por categorías** vista, el **nombre** propiedad en el **ToDo Fields** es de categoría seleccionado y la descripción de la **nombre** propiedad se muestra en la parte inferior de la ventana.

     ![Ventana propiedades](../extensibility/media/t5properties.png "T5Properties")

2. Agregue las siguientes instrucciones using el *TodoItem.cs* archivo.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Agregar el `public` modificador de acceso a la declaración de clase.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Agregue las dos propiedades, `Name` y `DueDate`. Haremos la `UpdateList()` y `CheckForErrors()` más adelante.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Agregue una referencia al control de usuario privada. Agregue un constructor que toma el control de usuario y el nombre para este elemento de lista de tareas. Para buscar el valor para `daysAhead`, obtiene la propiedad de la página de opciones.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Porque las instancias de la `TodoItem` clase se almacenarán en el cuadro de lista y el cuadro de lista llamará el `ToString` función, debe sobrecargar el `ToString` función. Agregue el código siguiente al *TodoItem.cs*, después del constructor y antes del final de la clase.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. En *TodoWindowControl.xaml.cs*, agregue los métodos de código auxiliar a la `TodoWindowControl` de clases para el `CheckForError` y `UpdateList` métodos. Colóquelos después el ProcessDialogChar y antes del final del archivo.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     El `CheckForError` método llamará a un método que tiene el mismo nombre en el objeto primario, y ese método comprobará si los errores se han producido y controlan correctamente. El `UpdateList` método actualizará el cuadro de lista en el control primario; el método se llama cuando el `Name` y `DueDate` las propiedades de este cambio de la clase. Que se implementarán más adelante.

## <a name="integrate-into-the-properties-window"></a>Integrar en la ventana Propiedades
 Ahora, escribir el código que administra el control ListBox, que estarán vinculado a la **propiedades** ventana.

 Debe cambiar el botón haga clic en el controlador para leer el cuadro de texto, cree una tarea pendiente y lo agrega al cuadro de lista.

1. Reemplazar existente `button1_Click` función con código que crea un nuevo TodoItem y lo agrega al cuadro de lista. Llama a `TrackSelection()`, que se definirán más adelante.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. En la vista Diseño, seleccione el control ListBox. En el **propiedades** ventana haga clic en el **controladores de eventos** botón y busque el **SelectionChanged** eventos. Rellene el cuadro de texto con **listBox_SelectionChanged**. Esto agrega un código auxiliar para un controlador de evento SelectionChanged y lo asigna al evento.

3. Implemente el método `TrackSelection()`. Dado que necesita obtener el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servicios, tiene que realizar la <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> accesible por el TodoWindowControl. Agregue el método siguiente a la `TodoWindow` clase:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Agregue las siguientes instrucciones using a *TodoWindowControl.xaml.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Rellene el controlador de evento SelectionChanged como sigue:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Ahora, rellene la función TrackSelection, que ofrecerá la integración con el **propiedades** ventana. Esta función se invoca cuando el usuario agrega un elemento al cuadro de lista o hace clic en un elemento en el cuadro de lista. Agrega el contenido del cuadro de lista a un SelectionContainer y pasa el SelectionContainer a la **propiedades** la ventana <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> controlador de eventos. El servicio TrackSelection realiza un seguimiento de los objetos seleccionados en la interfaz de usuario (UI) y muestra sus propiedades

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Ahora que tiene una clase que la **propiedades** puede usar la ventana, puede integrar el **propiedades** ventana con la ventana de herramientas. Cuando el usuario hace clic en un elemento en el cuadro de lista en la ventana de herramientas, el **propiedades** ventana debe actualizarse como corresponda. De forma similar, cuando el usuario cambia un elemento de lista de tareas en el **propiedades** ventana, se debe actualizar el elemento asociado.

7. Ahora, agregue el resto del código de la función UpdateList *TodoWindowControl.xaml.cs*. Debe quitar y volver a agregar TodoItem modificado desde el cuadro de lista.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Probar el código. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

9. Abra el **herramientas** > **opciones** página. Debería ver la categoría de lista de tareas en el panel izquierdo. Las categorías se muestran en orden alfabético, por lo que busque en el Ts.

10. En el **Todo** página de opciones, debería ver el `DaysAhead` propiedad establecida en **0**. Cámbielo a **2**.

11. En el **vista / Windows otras** menú Abrir **TodoWindow**. Tipo **EndDate** en el cuadro de texto y haga clic en **agregar**.

12. En el cuadro de lista debería ver una fecha de dos días posterior a la actual.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Agregar texto a la ventana de salida y los elementos de la lista de tareas
 Para el **lista de tareas**, cree un nuevo objeto de tipo de tarea y, a continuación, agregue ese objeto de tarea a la **lista de tareas** mediante una llamada a su `Add` método. Para escribir en el **salida** ventana, se llama a su `GetPane` llame al método para obtener un objeto de panel y, a continuación, el `OutputString` método del objeto de panel.

1. En *TodoWindowControl.xaml.cs*, en el `button1_Click` método, agregue código para obtener el **General** panel de la **salida** ventana (que es el valor predeterminado) y escribir en él. El método debe tener este aspecto:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Para agregar elementos a la lista de tareas, necesitará una para agregar una clase anidada a la clase TodoWindowControl. Debe derivar de la clase anidada <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Agregue el código siguiente al final de la `TodoWindowControl` clase.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. A continuación, agregue una referencia privada a `TodoTaskProvider` y un `CreateProvider()` método a la `TodoWindowControl` clase. El código debe tener este aspecto:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Agregar `ClearError()`, que borra la lista de tareas, y `ReportError()`, que agrega una entrada a la lista de tareas a la `TodoWindowControl` clase.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Ahora implemente el `CheckForErrors` método, como se indica a continuación.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Pruébelo

1. Compile la solución y comience la depuración. Aparece la instancia experimental.

2. Abra el **TodoWindow** (**vista** > **otros Windows** > **TodoWindow**).

3. Escriba algo en el cuadro de texto y, a continuación, haga clic en **agregar**.

     Una fecha de vencimiento 2 días después de hoy en día se agrega al cuadro de lista. No se generan errores y el **lista de tareas** (**vista** > **lista de tareas**) no debe tener ninguna entrada.

4. Ahora, cambie la configuración en el **herramientas** > **opciones** > **ToDo** página desde **2** a **0**.

5. Escriba algo más en el **TodoWindow** y, a continuación, haga clic en **agregar** nuevo. Esto desencadena un error y una entrada en el **lista de tareas**.

     A medida que agrega elementos, la fecha inicial se establece en ahora más de 2 días.

6. En el **vista** menú, haga clic en **salida** para abrir el **salida** ventana.

     Tenga en cuenta que cada vez que agregue un elemento, se muestra un mensaje en el **lista de tareas** panel.

7. Haga clic en uno de los elementos en el cuadro de lista.

     El **propiedades** ventana muestra las dos propiedades para el elemento.

8. Cambie una de las propiedades y, a continuación, presione **ENTRAR**.

     El elemento se actualiza en el cuadro de lista.
