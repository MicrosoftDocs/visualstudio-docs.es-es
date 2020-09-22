---
title: Extender las propiedades, los Lista de tareas, la salida y las ventanas de opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf42be1e62bfb4895d29a61fcadc221d5c14bec9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842735"
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Ampliación de las ventana Propiedades, Lista de tareas, Salida y Opciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede tener acceso a cualquier ventana de herramientas en Visual Studio. En este tutorial se muestra cómo integrar la información sobre la ventana de herramientas en una nueva página de **Opciones** y un nuevo valor en la página de **propiedades** , además de cómo escribir en las ventanas de **lista de tareas** y de **salida** .  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Crear una extensión con una ventana de herramientas  
  
1. Cree un proyecto denominado **ToDoList** mediante la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **TodoWindow**.  
  
    > [!NOTE]
    > Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Configurar la ventana de herramientas  
 Agregue un cuadro de texto en el que escribir un nuevo elemento ToDo, un botón para agregar el nuevo elemento a la lista y un cuadro de lista para mostrar los elementos de la lista.  
  
1. En TodoWindow. XAML, elimine los controles Button, TextBox y StackPanel del control UserControl.  
  
    > [!NOTE]
    > Esto no elimina el controlador de eventos **button1_Click** , que se reutilizará en un paso posterior.  
  
2. En la sección **todos los controles de WPF** del cuadro de **herramientas**, arrastre un control **Canvas** hasta la cuadrícula.  
  
3. Arrastre un **cuadro de texto**, un **botón**y un **cuadro de lista** al lienzo. Organice los elementos de modo que el cuadro de texto y el botón estén en el mismo nivel, y el control ListBox rellene el resto de la ventana debajo de ellos, como se muestra en la figura siguiente.  
  
     ![Ventana de herramientas terminada](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")  
  
4. En el panel XAML, busque el botón y establezca su propiedad de contenido en **Agregar**. Vuelva a conectar el controlador de eventos de botón al control de botón agregando un `Click="button1_Click"` atributo. El bloque Canvas debería tener este aspecto:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Personalizar el constructor  
  
1. En el archivo TodoWindowControl.xaml.cs, agregue la siguiente instrucción using:  
  
    ```csharp  
    using System;  
    ```  
  
2. Agregue una referencia pública a TodoWindow y haga que el constructor TodoWindowControl tome un parámetro TodoWindow. El código debe tener este aspecto:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3. En TodoWindow.cs, cambie el constructor TodoWindowControl para incluir el parámetro TodoWindow. El código debe tener este aspecto:  
  
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
 Puede proporcionar una página en el cuadro de diálogo **Opciones** para que los usuarios puedan cambiar la configuración de la ventana de herramientas. La creación de una página de opciones requiere tanto una clase que describa las opciones como una entrada en el archivo TodoListPackage.cs o TodoListPackage. VB.  
  
1. Agregue una clase denominada `ToolsOptions.cs`. Haga que la clase ToolsOptions herede de <xref:Microsoft.VisualStudio.Shell.DialogPage> .  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. Agregue la siguiente instrucción using:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. En la página Opciones de este tutorial solo se proporciona una opción denominada DaysAhead. Agregue un campo privado denominado **daysAhead** y una propiedad denominada **daysAhead** a la clase ToolsOptions:  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   Ahora debe hacer que el proyecto tenga en cuenta esta página de opciones.  
  
#### <a name="make-the-options-page-available-to-users"></a>Poner la Página opciones a disposición de los usuarios  
  
1. En TodoWindowPackage.cs, agregue <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la clase TodoWindowPackage:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2. El primer parámetro del constructor ProvideOptionPage es el tipo de la clase ToolsOptions, que ha creado anteriormente. El segundo parámetro, "ToDo", es el nombre de la categoría en el cuadro de diálogo **Opciones** . El tercer parámetro, "general", es el nombre de la subcategoría del cuadro de diálogo **Opciones** en el que estará disponible la página Opciones. Los dos parámetros siguientes son los identificadores de recursos de las cadenas; el primero es el nombre de la categoría y el segundo es el nombre de la subcategoría. El parámetro final determina si se puede tener acceso a esta página mediante automatización.  
  
     Cuando un usuario abre la página de opciones, debe ser similar a la siguiente imagen.  
  
     ![Página Opciones](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Observe la categoría **todo** y la subcategoría **General**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Hacer que los datos estén disponibles en la ventana Propiedades  
 Puede hacer que la información de la lista de tareas esté disponible mediante la creación de una clase denominada TodoItem que almacena información sobre los elementos individuales en la lista de tareas.  
  
1. Agregue una clase denominada `TodoItem.cs`.  
  
     Cuando la ventana de herramientas está disponible para los usuarios, los elementos del cuadro de lista se representarán mediante TodoItems. Cuando el usuario selecciona uno de estos elementos en el cuadro de lista, la ventana **propiedades** mostrará información sobre el elemento.  
  
     Para que los datos estén disponibles en la ventana **propiedades** , los datos se convierten en propiedades públicas que tienen dos atributos especiales, `Description` y `Category` . `Description` es el texto que aparece en la parte inferior de la ventana **propiedades** . `Category` determina dónde debe aparecer la propiedad cuando se muestra la ventana **propiedades** en la vista por **categorías** . En la imagen siguiente, la ventana **propiedades** está en la vista por **categorías** , se selecciona la propiedad **nombre** en la categoría campos de la lista de **tareas** y se muestra la descripción de la propiedad **nombre** en la parte inferior de la ventana.  
  
     ![Propiedades (ventana)](../extensibility/media/t5properties.png "T5Properties")  
  
2. Agregue las siguientes instrucciones using al archivo TodoItem.cs.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. Agregue el `public` modificador de acceso a la declaración de clase.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Agregue las dos propiedades, Name y DueDate. Más adelante, UpdateList () y CheckForErrors ().  
  
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
  
4. Agregue una referencia privada al control de usuario. Agregue un constructor que tome el control de usuario y el nombre de este elemento de la lista de tareas. Para buscar el valor de daysAhead, obtiene la propiedad de la página de opciones.  
  
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
  
5. Dado que las instancias de la `TodoItem` clase se almacenarán en el cuadro de lista y el control ListBox llamará a la `ToString` función, debe sobrecargar la `ToString` función. Agregue el código siguiente a TodoItem.cs, después del constructor y antes del final de la clase.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6. En TodoWindowControl.xaml.cs, agregue métodos de código auxiliar a la clase TodoWindowControl para los `CheckForError` `UpdateList` métodos y. Colóquelos después del ProcessDialogChar y antes del final del archivo.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     El `CheckForError` método llamará a un método que tiene el mismo nombre en el objeto primario y ese método comprobará si se ha producido algún error y los controlará correctamente. El `UpdateList` método actualizará el cuadro de lista en el control primario; se llama al método `Name` cuando `DueDate` cambian las propiedades y de esta clase. Se implementarán más adelante.  
  
## <a name="integrate-into-the-properties-window"></a>Integrar en la ventana Propiedades  
 Ahora escriba el código que administra el cuadro de lista, que se vinculará a la ventana **propiedades** .  
  
 Debe cambiar el controlador de clic de botón para leer el cuadro de texto, crear un TodoItem y agregarlo al cuadro de lista.  
  
1. Reemplace la `button1_Click` función existente por el código que crea un nuevo TodoItem y lo agrega al cuadro de lista. Llama a TrackSelection (), que se definirá más adelante.  
  
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
  
2. En el Vista de diseño Seleccione el control ListBox. En la ventana **propiedades** , haga clic en el botón **controladores de eventos** y busque el evento SelectionChanged. Rellene el cuadro de texto con **listBox_SelectionChanged**. Esto agrega un código auxiliar para un controlador de SelectionChanged y lo asigna al evento.  
  
3. Implemente el método TrackSelection (). Como necesitará obtener los <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servicios, necesitará que el <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl sea accesible. Agregue el método siguiente a la clase TodoWindow:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4. Agregue las siguientes instrucciones Using a TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5. Rellene el controlador de SelectionChanged como se indica a continuación:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6. Ahora, rellene la función TrackSelection, que proporcionará la integración con la ventana **propiedades** . Se llama a esta función cuando el usuario agrega un elemento al cuadro de lista o hace clic en un elemento del cuadro de lista. Agrega el contenido del control ListBox a SelectionContainer y pasa el SelectionContainer al controlador de eventos de la ventana **propiedades** <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> . El servicio TrackSelection realiza un seguimiento de los objetos seleccionados en la interfaz de usuario (UI) y muestra sus propiedades.  
  
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
  
     Ahora que tiene una clase que puede usar la ventana **propiedades** , puede integrar la ventana **propiedades** con la ventana de herramientas. Cuando el usuario hace clic en un elemento del cuadro de lista de la ventana de herramientas, la ventana **propiedades** debe actualizarse en consecuencia. Del mismo modo, cuando el usuario cambia un elemento ToDo en la ventana **propiedades** , se debe actualizar el elemento asociado.  
  
7. Ahora, agregue el resto del código de la función UpdateList en TodoWindowControl.xaml.cs. Debe quitar y volver a agregar el TodoItem modificado desde el cuadro de lista.  
  
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
  
9. Abra las páginas **herramientas/opciones** . Debería ver la categoría ToDo en el panel izquierdo. Las categorías se muestran en orden alfabético, así que mire en TS.  
  
10. En la página Opciones de tareas pendientes, debería ver la propiedad DaysAhead establecida en **0**. Cámbielo a **2**.  
  
11. En el menú Ver/otras ventanas, Abra **TodoWindow**. Escriba **EndDate** en el cuadro de texto y haga clic en **Agregar**.  
  
12. En el cuadro de lista debería ver una fecha dos días posterior a hoy.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Agregue texto al Ventana de salida y elementos al Lista de tareas  
 En el **lista de tareas**, cree un nuevo objeto de tipo Task y, a continuación, agregue ese objeto de tarea a la **lista de tareas** llamando a su método Add. Para escribir en la ventana de **salida** , llame a su método GetPane para obtener un objeto de panel y, a continuación, llame al método OutputString del objeto pane.  
  
1. En TodoWindowControl.xaml.cs, en el `button1_Click` método, agregue código para obtener el panel **General** de la ventana de **salida** (que es el valor predeterminado) y escriba en él. Este es el aspecto que debe tener el método:  
  
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
  
2. Para agregar elementos al Lista de tareas, necesita para agregar una clase anidada a la clase TodoWindowControl. La clase anidada debe derivar de <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Agregue el código siguiente al final de la clase TodoWindowControl.  
  
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
  
3. A continuación, agregue una referencia privada a TodoTaskProvider y un método CreateProvider () a la clase TodoWindowControl. El código debe tener este aspecto:  
  
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
  
4. Agregue ClearError (), que borra el Lista de tareas, y ReportError (), que agrega una entrada a la Lista de tareas, a la clase TodoWindowControl.  
  
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
  
5. Ahora, implemente el método CheckForErrors, como se indica a continuación.  
  
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
  
## <a name="trying-it-out"></a>Prueba  
  
1. Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
2. Abra TodoWindow (**Ver/otras ventanas/TodoWindow**).  
  
3. Escriba algo en el cuadro de texto y, a continuación, haga clic en **Agregar**.  
  
     Una fecha de vencimiento 2 días después de hoy se agrega al cuadro de lista. No se generan errores y el **lista de tareas** (**Ver/lista de tareas**) no debe tener ninguna entrada.  
  
4. Ahora, cambie el valor de la página **herramientas/opciones/todo** de **2** de nuevo a **0**.  
  
5. Escriba otra cosa en el **TodoWindow** y, a continuación, haga clic en **Agregar** de nuevo. Esto desencadena un error y también una entrada en el **lista de tareas**.  
  
     A medida que agrega elementos, la fecha inicial se establece en Now más 2 días.  
  
6. En el menú **Ver** , haga clic en **salida** para abrir la ventana **resultados** .  
  
     Tenga en cuenta que cada vez que se agrega un elemento, se muestra un mensaje en el panel **lista de tareas** .  
  
7. Haga clic en uno de los elementos del cuadro de lista.  
  
     La ventana **propiedades** muestra las dos propiedades del elemento.  
  
8. Cambie una de las propiedades y, a continuación, presione Entrar.  
  
     El elemento se actualiza en el cuadro de lista.
