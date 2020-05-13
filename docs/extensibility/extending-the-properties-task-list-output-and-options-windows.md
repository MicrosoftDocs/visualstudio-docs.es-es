---
title: Ampliar las ventanas Propiedades, Lista de tareas, Salida, Opciones
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711635"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Amplíe las ventanas Propiedades, Lista de tareas, Salida y Opciones
Puede tener acceso a cualquier ventana de herramientas en Visual Studio. En este tutorial se muestra cómo integrar información sobre la ventana de herramientas en una nueva página **Opciones** y una nueva configuración en la página **Propiedades,** así como cómo escribir en las ventanas **Lista** de tareas y **Salida.**

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-an-extension-with-a-tool-window"></a>Crear una extensión con una ventana de herramientas

1. Cree un proyecto denominado **TodoList** con la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **TodoWindow**.

    > [!NOTE]
    > Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, consulte [Crear una extensión con una ventana](../extensibility/creating-an-extension-with-a-tool-window.md)de herramientas .

## <a name="set-up-the-tool-window"></a>Configurar la ventana de herramientas
 Agregue un cuadro de texto en el que escribir un nuevo elemento de tareas pendientes, un botón para agregar el nuevo elemento a la lista y un listbox para mostrar los elementos de la lista.

1. En *TodoWindow.xaml*, elimine los controles Button, TextBox y StackPanel de UserControl.

    > [!NOTE]
    > Esto no elimina el controlador de eventos **button1_Click,** que reutilizará en un paso posterior.

2. En la sección **Todos los controles WPF** del Cuadro de **herramientas**, arrastre un control **Canvas** a la cuadrícula.

3. Arrastre un cuadro de **texto**, un **botón**y un **cuadro de** lista al lienzo. Organice los elementos para que el cuadro de texto y el botón están en el mismo nivel y el ListBox rellena el resto de la ventana debajo de ellos, como en la imagen siguiente.

     ![Ventana de herramientas terminada](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. En el panel XAML, busque Button y establezca su content propiedad **Add**. Vuelva a conectar el controlador de eventos `Click="button1_Click"` button al control Button agregando un atributo. El bloque Canvas debería tener este aspecto:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personalizar el constructor

1. En el archivo *TodoWindowControl.xaml.cs,* agregue la siguiente directiva using:

    ```csharp
    using System;
    ```

2. Agregue una referencia pública a TodoWindow y haga que el TodoWindowControl constructor tome un TodoWindow parámetro. El código debe tener este aspecto:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. En *TodoWindow.cs*, cambie TodoWindowControl constructor para incluir el TodoWindow parámetro. El código debe tener este aspecto:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Crear una página Opciones
 Puede proporcionar una página en el cuadro de diálogo **Opciones** para que los usuarios puedan cambiar la configuración de la ventana de herramientas. Crear una página Options requiere una clase que describa las opciones y una entrada en el *archivo TodoListPackage.cs* o *TodoListPackage.vb.*

1. Agregue una clase denominada `ToolsOptions.cs`. Haga `ToolsOptions` que la <xref:Microsoft.VisualStudio.Shell.DialogPage>clase herede de .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Agrega la siguiente directiva de uso:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. La página Opciones de este tutorial solo proporciona una opción denominada DaysAhead. Agregue un campo privado denominado **daysAhead** y `ToolsOptions` una propiedad denominada **DaysAhead** a la clase:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Ahora debe hacer que el proyecto tenga en cuenta esta página Opciones.

### <a name="make-the-options-page-available-to-users"></a>Haga que la página Opciones esté disponible para los usuarios

1. En *TodoWindowPackage.cs*, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> agregue `TodoWindowPackage` a la clase:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. El primer parámetro para el ProvideOptionPage constructor `ToolsOptions`es el tipo de la clase , que creó anteriormente. El segundo parámetro, "ToDo", es el nombre de la categoría en el cuadro de diálogo **Opciones.** El tercer parámetro, "General", es el nombre de la subcategoría del cuadro de diálogo **Opciones** donde estará disponible la página Opciones. Los dos parámetros siguientes son identificadores de recursos para cadenas; el primero es el nombre de la categoría, y el segundo es el nombre de la subcategoría. El parámetro final determina si se puede acceder a esta página mediante la automatización.

     Cuando un usuario abre la página Opciones, debe ser similar a la siguiente imagen.

     ![Página Opciones](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Observe la categoría **ToDo** y la subcategoría **General**.

## <a name="make-data-available-to-the-properties-window"></a>Poner los datos a disposición de la ventana Propiedades
 Puede hacer que la información de la `TodoItem` lista de tareas pendientes esté disponible mediante la creación de una clase denominada que almacena información sobre los elementos individuales en la lista Tareas pendientes.

1. Agregue una clase denominada `TodoItem.cs`.

     Cuando la ventana de herramientas está disponible para los usuarios, los elementos de la ListBox se representarán por TodoItems. Cuando el usuario selecciona uno de estos elementos en el ListBox, la ventana **Propiedades** mostrará información sobre el elemento.

     Para que los datos estén disponibles en la ventana **Propiedades,** convierta los datos en propiedades públicas que tengan dos atributos especiales `Description` y `Category`. `Description`es el texto que aparece en la parte inferior de la ventana **Propiedades.** `Category`determina dónde debe aparecer la propiedad cuando se muestra la ventana **Propiedades** en la vista **Clasificado.** En la siguiente imagen, la ventana **Propiedades** se encuentra en la vista **Clasificado,** la propiedad **Nombre** de la categoría Campos de **torsión** está seleccionada y la descripción de la propiedad **Nombre** se muestra en la parte inferior de la ventana.

     ![Ventana Propiedades](../extensibility/media/t5properties.png "T5Properties")

2. Agregue las siguientes directivas using el archivo *TodoItem.cs.*

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Agregue `public` el modificador de acceso a la declaración de clase.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Agregue las dos `Name` `DueDate`propiedades y . Haremos lo `UpdateList()` y `CheckForErrors()` más tarde.

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

4. Agregue una referencia privada al control de usuario. Agregue un constructor que tome el control de usuario y el nombre de este elemento ToDo. Para encontrar el `daysAhead`valor de , obtiene la propiedad de página Opciones.

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

5. Dado que las `TodoItem` instancias de la clase se almacenarán `ToString` en el ListBox `ToString` y el ListBox llamará a la función, debe sobrecargar la función. Agregue el código siguiente a *TodoItem.cs*, después del constructor y antes del final de la clase.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. En *TodoWindowControl.xaml.cs*, agregue métodos de código auxiliar a `TodoWindowControl` la clase para los `CheckForError` métodos y. `UpdateList` Colóquelos después de ProcessDialogChar y antes del final del archivo.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     El `CheckForError` método llamará a un método que tenga el mismo nombre en el objeto primario y ese método comprobará si se han producido errores y los controlará correctamente. El `UpdateList` método actualizará el ListBox en el control primario; se llama al `Name` método `DueDate` cuando cambian las propiedades y de esta clase. Se implementarán más adelante.

## <a name="integrate-into-the-properties-window"></a>Integrar en la ventana Propiedades
 Ahora escriba el código que administra el ListBox, que se vinculará a la **ventana Propiedades.**

 Debe cambiar el controlador de clic de botón para leer el cuadro de texto, crear un TodoItemy lo agrega a la ListBox.

1. Reemplace la `button1_Click` función existente con código que crea un nuevo TodoItem y lo agrega a ListBox. Llama `TrackSelection()`a , que se definirá más adelante.

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

2. En la vista Diseño, seleccione el control ListBox. En la ventana **Propiedades,** haga clic en el botón **Controladores** de eventos y busque el evento **SelectionChanged.** Rellene el cuadro de texto con **listBox_SelectionChanged**. Al hacerlo, se agrega un código auxiliar para un SelectionChanged controlador y se asigna al evento.

3. Implemente el método `TrackSelection()`. Puesto que necesitará obtener <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> los servicios, <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> necesita hacer que el accesible por el TodoWindowControl. Agregue el siguiente método a la clase `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Agregue las siguientes directivas using a *TodoWindowControl.xaml.cs:*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Rellene el selectionChanged controlador de la siguiente manera:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Ahora, rellene la función TrackSelection, que proporcionará integración con la ventana **Propiedades.** Esta función se llama cuando el usuario agrega un elemento a la ListBox o hace clic en un elemento en el ListBox. Agrega el contenido de la ListBox a un SelectionContainer y pasa el <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> SelectionContainer al controlador de eventos de la ventana **Properties.** El servicio TrackSelection realiza un seguimiento de los objetos seleccionados en la interfaz de usuario (UI) y muestra sus propiedades

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

     Ahora que tiene una clase que puede usar la ventana **Propiedades,** puede integrar la ventana **Propiedades** con la ventana de herramientas. Cuando el usuario hace clic en un elemento en el ListBox en la ventana de herramientas, la ventana **Propiedades** debe actualizarse en consecuencia. De forma similar, cuando el usuario cambia un elemento de tareas pendientes en el **propiedades** ventana, el elemento asociado debe actualizarse.

7. Ahora, agregue el resto del código de la función UpdateList en *TodoWindowControl.xaml.cs*. Debe quitar y volver a agregar el TodoItem modificado desde el ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Pruebe el código. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

9. Abra la página**Opciones de** **herramientas.** >  Debería ver la categoría Tareas pendientes en el panel izquierdo. Las categorías se enumeran alfabéticamente, así que mire bajo las Ts.

10. En la página Opciones de `DaysAhead` **Todo,** debería ver la propiedad establecida en **0**. Cámbielo a **2**.

11. En el menú **Ver / Otras ventanas,** abra **TodoWindow**. Escriba **EndDate** en el cuadro de texto y haga clic en **Agregar**.

12. En el cuadro de lista debería ver una fecha dos días después de hoy.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Agregue texto a la ventana Salida y elementos a la Lista de tareas
 Para la lista de **tareas**, cree un nuevo objeto de tipo Task y, a continuación, agregue ese objeto Task a la **lista** de tareas llamando a su `Add` método. Para escribir en el **salida** `GetPane` ventana, llame a su método para `OutputString` obtener un objeto de panel y, a continuación, llame al método del objeto de panel.

1. En *TodoWindowControl.xaml.cs*, `button1_Click` en el método, agregue código para obtener el panel **General** de **la** salida ventana (que es el valor predeterminado) y escribir en él. Este es el aspecto que debe tener el método:

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

2. Para agregar elementos a la lista de tareas, necesita a para agregar una clase anidada a la TodoWindowControl clase. La clase anidada debe <xref:Microsoft.VisualStudio.Shell.TaskProvider>derivar de . Agregue el código siguiente al `TodoWindowControl` final de la clase.

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

3. A continuación, agregue `TodoTaskProvider` una `CreateProvider()` referencia `TodoWindowControl` privada y un método a la clase. El código debe tener este aspecto:

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

4. Agregar `ClearError()`, que borra la `ReportError()`lista de tareas y , que agrega `TodoWindowControl` una entrada a la lista de tareas, a la clase.

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

5. Ahora implemente `CheckForErrors` el método, como se indica a continuación.

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

## <a name="try-it-out"></a>Prueba

1. Compile la solución y comience la depuración. Aparece la instancia experimental.

2. Abra **TodoWindow** (**Ver** > **otras ventanas** > **TodoWindow**).

3. Escriba algo en el cuadro de texto y, a continuación, haga clic en **Agregar**.

     Una fecha de vencimiento 2 días después de hoy se agrega al cuadro de lista. No se generan errores y la **lista** de tareas **(Ver** > **lista**de tareas ) no debe tener entradas.

4. Ahora cambie la configuración en **la** > página**Opciones** > de herramientas**para hacer** de **2** a **0**.

5. Escriba algo más en **TodoWindow** y, a continuación, haga clic en **Agregar** de nuevo. Esto desencadena un error y también una entrada en la **lista de tareas**.

     A medida que agrega elementos, la fecha inicial se establece en ahora más 2 días.

6. En el menú **Ver,** haga clic en **Salida** para abrir la ventana **Salida.**

     Tenga en cuenta que cada vez que agrega un elemento, se muestra un mensaje en el panel Lista de **tareas.**

7. Haga clic en uno de los elementos del cuadro de lista.

     La ventana **Propiedades** muestra las dos propiedades del elemento.

8. Cambie una de las propiedades y, a continuación, pulse **Intro**.

     El elemento se actualiza en el ListBox.
