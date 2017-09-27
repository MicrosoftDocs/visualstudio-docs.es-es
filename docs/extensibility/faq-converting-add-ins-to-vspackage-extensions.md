---
title: "Preguntas más frecuentes: Conversión de complementos a las extensiones del VSPackage | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 22
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 8db7d203b599c11ce8fea07ed3647771c879a256
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Preguntas más frecuentes: Convertir complementos en extensiones de VSPackage
Los complementos están desusados. Para realizar una nueva extensión de Visual Studio, debe crear una extensión VSIX. Aquí están las respuestas a algunas preguntas frecuentes acerca de cómo convertir un complemento de Visual Studio en una extensión VSIX.  
  
> [!WARNING]
>  A partir de Visual Studio 2015, para los proyectos de C# y Visual Basic, puede usar el proyecto VSIX y agregar plantillas de elementos para los comandos de menú, ventanas de herramientas y VSPackages. Para obtener más información, consulte [What's New en Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  En muchos casos puede transferir simplemente el código de complemento a un proyecto VSIX con un elemento de proyecto de VSPackage. Puede obtener el objeto de automatización DTE mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> en el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Para obtener más información, consulte [¿Cómo ejecuto mi código de complementos en un paquete VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) a continuación.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>¿Qué software es necesario desarrollar las extensiones VSIX?  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>¿Dónde está la documentación de la extensión?  
 Comience con [empezando a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Otros artículos acerca del desarrollo de la extensión VSSDK en MSDN están por debajo de la que uno.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>¿Puedo convertir mi proyecto de complemento en un proyecto VSIX?  
 Un proyecto de complemento no se puede convertir directamente a un proyecto VSIX porque los mecanismos utilizados en proyectos VSIX no son los mismos que los de los proyectos de complemento. La plantilla de proyecto VSIX, además de las plantillas de elementos de proyecto derecha tienen una gran cantidad de código que facilita relativamente fáciles de desarrollar y la ejecución como una extensión VSIX.  
  
##  <a name="BKMK_StartDeveloping"></a>¿Cómo empezar a desarrollar las extensiones VSIX?  
 Le mostramos cómo realizar una extensión VSIX que tiene un comando de menú:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Para conseguir una extensión VSIX tiene un comando de menú  
  
1.  Crear un proyecto de VSIX. (**Archivo**, **New**, **proyecto**, o tipo **proyecto** en el **inicio rápido** ventana). En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C# / extensibilidad** o **Visual Basic / extensibilidad** y seleccione **proyecto VSIX**.) Denomine el proyecto **TestExtension** y especifique una ubicación para él.  
  
2.  Agregar un **comando personalizado** plantilla de elemento de proyecto. (Haga clic en el nodo de proyecto en el **el Explorador de soluciones** y seleccione **Agregar / nuevo elemento**. En el **nuevo proyecto** cuadro de diálogo de Visual C# o Visual Basic, seleccione el **extensibilidad** nodo y seleccione **comando personalizado**.)  
  
3.  Presione F5 para compilar y ejecutar el proyecto en modo de depuración.  
  
     Se muestra una segunda instancia de Visual Studio. Esta segunda instancia se llama instancia experimental, y puede que no tenga la misma configuración que la instancia de Visual Studio que está usando para escribir código. La primera vez que ejecute la instancia experimental se le pedirá que inicie sesión en VS Online y especifique el tema y el perfil.  
  
     En el **herramientas** menú (en la instancia experimental) debería ver un botón denominado **nombre de comando mi**. Al elegir este botón, debería aparecer un mensaje: **en TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="BKMK_RunAddin"></a>¿Cómo se puede ejecutar el código del complemento en un paquete VSPackage?  
 Normalmente, el código de complemento normalmente se ejecuta de una de dos maneras:  
  
-   Se desencadena mediante un comando de menú (el código está en el método `IDTCommandTarget.Exec`)  
  
-   Automáticamente en el inicio (el código está en el controlador del evento `OnConnection`).  
  
 Puede hacer las mismas cosas en un VSPackage. Aquí se indica cómo agregar código de complemento en el método de devolución de llamada:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Para implementar un comando de menú en un VSPackage  
  
1.  Cree un VSPackage que tenga un comando de menú. (Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Abra el archivo que contiene la definición del VSPackage. (En un proyecto de C#, tiene * \<el nombre del proyecto >*Package.cs.)  
  
3.  Agregue las siguientes instrucciones `using` al archivo:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Busque el método `MenuItemCallback`. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Agregue el código que el complemento tenía en su método `IDTCommandTarget.Exec`. Por ejemplo, aquí es parte del código que agrega un nuevo panel a la **salida** ventana e imprime "Some Text" en el panel de nuevo.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Compile y ejecute este proyecto. Presione F5 o seleccione **iniciar** en el **depurar** barra de herramientas. En la instancia experimental de Visual Studio, el **herramientas** menú debe tener un botón denominado **nombre de comando mi**. Al elegir este botón, las palabras **texto algunas** debe aparecer en una **salida** panel de ventana. (Puede que tenga que abrir la **salida** ventana.)  
  
 También puede hacer que el código se ejecute en el inicio. Sin embargo, normalmente eso se desaconseja para las extensiones VSPackage. Si se intentan cargar demasiadas extensiones cuando se inicia Visual Studio, el tiempo de inicio será notablemente mayor. El procedimiento recomendado es cargar el VSPackage automáticamente solo cuando se cumpla alguna condición (por ejemplo, que se abra una solución).  
  
 Este procedimiento muestra cómo ejecutar código de complemento en un VSPackage que se carga automáticamente cuando se abre una solución:  
  
#### <a name="to-autoload-a-vspackage"></a>Para cargar automáticamente un VSPackage  
  
1.  Cree un proyecto VSIX con un elemento de proyecto de paquete de Visual Studio. (Para que conocer los pasos hacerlo, consulte [¿cómo empiezo desarrollar extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Basta con agregar el **paquete de Visual Studio** de elementos de proyecto en su lugar.) Denomine el proyecto VSIX **TestAutoload**.  
  
2.  Abra TestAutoloadPackage.cs. Encuentre la línea donde se declara la clase de paquete:  
  
    ```csharp  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Por encima de esta línea hay un conjunto de atributos. Agregue este atributo:  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Establezca un punto de interrupción en el método `Initialize()` e inicie la depuración (F5).  
  
5.  En la instancia experimental, abra un proyecto. El VSPackage se cargará y se alcanzará el punto de interrupción.  
  
 Para especificar otros contextos en los que cargar su VSPackage, puede usar los campos de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Para obtener más información, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>¿Cómo obtengo el objeto DTE?  
 Si el complemento no muestra una interfaz de usuario (por ejemplo, comandos de menú, botones de barra de herramientas o ventanas de herramienta) quizás pueda usar el código tal cual siempre que obtenga el objeto de automatización DTE del VSPackage. Esta es la manera de hacerlo:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Para obtener el objeto DTE de un VSPackage  
  
1.  En un proyecto VSIX, con una plantilla de elementos de paquete de Visual Studio, busque el * \<nombre del proyecto >*Package.cs archivo. Esta es la clase que deriva de <xref:Microsoft.VisualStudio.Shell.Package>; puede ayudarlo a interaccionar con Visual Studio. En este caso, usa su <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>.  
  
2.  Agregue estas instrucciones `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Busque el método `Initialize`. Este método controla el comando que especificó en el asistente para paquetes. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto DTE:  
  
    ```csharp  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Cuando tenga el objeto de automatización <xref:EnvDTE.DTE>, puede agregar el resto del código de complemento al proyecto. Si necesita el objeto <xref:EnvDTE80.DTE2>, puede hacer lo mismo.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>¿Cómo cambio los comandos de menú y los botones de barra de herramientas en mi complemento al estilo de VSPackage?  
 Las extensiones VSPackage usan el archivo .vsct para crear la mayoría de los comandos de menú, barras de herramientas, botones de barra de herramientas y otras interfaces de usuario. El **comando personalizado** plantilla de elemento de proyecto ofrece la opción para crear un comando en el **herramientas** menú. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información acerca de los archivos de vsct, consulte [cómo VSPackages agregar elementos de la interfaz](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Para ver tutoriales que muestran cómo usar el archivo .vsct para agregar elementos de menú, barras de herramientas y botones de barra de herramientas, consulte [extender menús y comandos de](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>¿Cómo agrego ventanas de herramienta personalizadas a la manera de VSPackage?  
 La plantilla de elemento de proyecto de ventana de herramientas personalizada le ofrece la opción para crear una ventana de herramientas. Para obtener más información acerca de esta plantilla de elemento de proyecto, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md). Para obtener información acerca de las ventanas de herramientas, consulte [ampliar y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md) y los artículos, especialmente [agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>¿Cómo administro las ventanas de Visual Studio a la manera de VSPackage?  
 Si su complemento administra las ventanas de Visual Studio, el código de complemento debería funcionar en un VSPackage. Por ejemplo, este procedimiento muestra cómo agregar código que administra el **lista de tareas** a la `MenuItemCallback` método de VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Para insertar código de administración de ventanas desde un complemento en un VSPackage  
  
1.  Crear un VSPackage que tiene un comando de menú, como en el [¿cómo empiezo desarrollar extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sección.  
  
2.  Abra el archivo que contiene la definición del VSPackage. (En un proyecto de C#, tiene * \<el nombre del proyecto >*Package.cs.)  
  
3.  Agregue estas instrucciones `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Busque el método `MenuItemCallback`. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Agregue el código de su complemento. Por ejemplo, este es el código que agrega nuevas tareas para el **lista de tareas**, muestra el número de tareas y, a continuación, elimina una tarea.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)   
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
        askItem tlItem;   
  
        // Add a couple of tasks to the Task List.   
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
            true, "", 10, true, true);  
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
        // List the total number of task list items after adding the new task items.  
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
        // Remove the second task item. The items list in reverse numeric order.   
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
        tl.TaskItems.Item(2).Delete();  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
    }  
    ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>¿Cómo administro proyectos y soluciones en un VSPackage?  
 Si su complemento administra proyectos y soluciones, el código de complemento debería funcionar en un VSPackage. Por ejemplo, este procedimiento muestra cómo agregar código que obtiene el proyecto de inicio.  
  
1.  Crear un VSPackage que tiene un comando de menú, como en el [¿cómo empiezo desarrollar extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sección.  
  
2.  Abra el archivo que contiene la definición del VSPackage. (En un proyecto de C#, tiene * \<el nombre del proyecto >*Package.cs.)  
  
3.  Agregue estas instrucciones `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Busque el método `MenuItemCallback`. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Agregue el código de su complemento. Por ejemplo, el siguiente código obtiene el nombre del proyecto de inicio en una solución. (Se debe abrir una solución multiproyecto cuando este paquete se ejecuta).  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
        Project startupProj;   
        string msg = "";  
  
        foreach (String item in (Array)sb.StartupProjects)   
        {  
            msg += item;   
        }  
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
        startupProj = dte.Solution.Item(msg);   
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
    }  
    ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>¿Cómo establezco métodos abreviados de teclado en un VSPackage?  
 Se usa el elemento `<KeyBindings>` del archivo .vsct. En el ejemplo siguiente, el método abreviado de teclado para el comando `idCommand1` es Alt+A, y el método abreviado de teclado para el comando `idCommand2` es Alt+Ctrl+A. Tenga en cuenta la sintaxis de los nombres de clave.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>¿Cómo administro los eventos de automatización en un VSPackage?  
 Los eventos de automatización en un VSPackage se controlan de la misma manera que en el complemento. En el código siguiente se muestra cómo controlar el evento `OnItemRenamed`. (En el ejemplo se da por hecho que ya ha obtenido el objeto DTE).  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
