---
title: 'Preguntas más frecuentes: convertir complementos en extensiones VSPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843058"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Preguntas más frecuentes: Convertir complementos en extensiones de VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los complementos están desusados. Para crear una nueva extensión de Visual Studio, debe crear una extensión VSIX. Estas son las respuestas a algunas preguntas frecuentes sobre cómo convertir un complemento de Visual Studio en una extensión VSIX.  
  
> [!WARNING]
> A partir de Visual Studio 2015, para los proyectos de C# y Visual Basic, puede usar el Proyecto VSIX y agregar plantillas de elementos para los comandos de menú, las ventanas de herramientas y los VSPackages. Para obtener más información, vea [What's New in the Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
> En muchos casos, puede simplemente transferir el código del complemento a un proyecto de VSIX con un elemento de proyecto de VSPackage. Puede obtener el objeto de automatización DTE mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> en el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Para obtener más información, vea [¿Cómo puedo ejecutar el código de mi complemento en un VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) a continuación.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>¿Qué software necesito para desarrollar extensiones VSIX?  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>¿Dónde está la documentación de la extensión?  
 Comience [a empezar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Otros artículos sobre el desarrollo de extensiones de VSSDK en MSDN están por debajo de ese mismo.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>¿Puedo convertir mi proyecto de complemento en un proyecto VSIX?  
 Un proyecto de complemento no se puede convertir directamente en un proyecto VSIX porque los mecanismos que se usan en proyectos VSIX no son los mismos que los de los proyectos de complementos. La plantilla de Proyecto VSIX, además de las plantillas de elementos de proyecto adecuadas, tienen una gran cantidad de código que hace que sea relativamente fácil empezar a trabajar como una extensión VSIX.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> Cómo empezar a desarrollar extensiones VSIX?  
 Aquí se muestra cómo crear un VSIX que tenga un comando de menú:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Para crear una extensión VSIX que tenga un comando de menú  
  
1. Crear un proyecto de VSIX. (**Archivo**, **nuevo**, **proyecto**o escriba **proyecto** en la ventana **Inicio rápido** ). En el cuadro de diálogo **nuevo proyecto** , expanda **Visual C#/extensibilidad** o **Visual Basic/Extensibility** y seleccione **Proyecto VSIX**). Asigne al proyecto el nombre **TestExtension** y especifique una ubicación para él.  
  
2. Agregue una plantilla de elemento de proyecto de **comando personalizado** . (Haga clic con el botón secundario en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Agregar o nuevo elemento**. En el cuadro de diálogo **nuevo proyecto** de Visual C# o Visual Basic, seleccione el nodo **extensibilidad** y seleccione **comando personalizado**).  
  
3. Presione F5 para compilar y ejecutar el proyecto en modo de depuración.  
  
     Se muestra una segunda instancia de Visual Studio. Esta segunda instancia se llama instancia experimental, y puede que no tenga la misma configuración que la instancia de Visual Studio que está usando para escribir código. La primera vez que ejecute la instancia experimental se le pedirá que inicie sesión en VS Online y especifique el tema y el perfil.  
  
     En el menú **herramientas** (en la instancia experimental) debería ver un botón denominado **My Command Name**. Al elegir este botón, debe aparecer un mensaje: **dentro de TestVSPackagePackage. MenuItemCallback ()**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> ¿Cómo se puede ejecutar el código de complemento en un VSPackage?  
 Normalmente, el código de complemento normalmente se ejecuta de una de dos maneras:  
  
- Se desencadena mediante un comando de menú (el código está en el método `IDTCommandTarget.Exec`)  
  
- Automáticamente en el inicio (el código está en el controlador del evento `OnConnection`).  
  
  Puede hacer las mismas cosas en un VSPackage. Aquí se indica cómo agregar código de complemento en el método de devolución de llamada:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Para implementar un comando de menú en un VSPackage  
  
1. Cree un VSPackage que tenga un comando de menú. (Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)).  
  
2. Abra el archivo que contiene la definición del VSPackage. (En un proyecto de C#, <em>\<your project name></em> es Package.cs).  
  
3. Agregue las siguientes instrucciones `using` al archivo:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Busque el método `MenuItemCallback`. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Agregue el código que el complemento tenía en su método `IDTCommandTarget.Exec`. Por ejemplo, este es un código que agrega un nuevo panel a la ventana de **salida** e imprime "texto en el panel nuevo".  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Compile y ejecute este proyecto. Presione F5 o seleccione **iniciar** en la barra de herramientas **depurar** . En la instancia experimental de Visual Studio, el menú **herramientas** debe tener un botón denominado **My Command Name**. Al elegir este botón, la palabra **texto** debe aparecer en un panel de la ventana de **salida** . (Es posible que tenga que abrir la ventana de **salida** ).  
  
   También puede hacer que el código se ejecute en el inicio. Sin embargo, normalmente eso se desaconseja para las extensiones VSPackage. Si se intentan cargar demasiadas extensiones cuando se inicia Visual Studio, el tiempo de inicio será notablemente mayor. El procedimiento recomendado es cargar el VSPackage automáticamente solo cuando se cumpla alguna condición (por ejemplo, que se abra una solución).  
  
   Este procedimiento muestra cómo ejecutar código de complemento en un VSPackage que se carga automáticamente cuando se abre una solución:  
  
#### <a name="to-autoload-a-vspackage"></a>Para cargar automáticamente un VSPackage  
  
1. Cree un proyecto VSIX con un elemento de proyecto de paquete de Visual Studio. (Para conocer los pasos para hacerlo, vea [Cómo empezar a desarrollar extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Solo tiene que agregar el elemento de proyecto del **paquete de Visual Studio** en su lugar). Asigne al Proyecto VSIX el nombre **TestAutoload**.  
  
2. Abra TestAutoloadPackage.cs. Encuentre la línea donde se declara la clase de paquete:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Por encima de esta línea hay un conjunto de atributos. Agregue este atributo:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Establezca un punto de interrupción en el método `Initialize()` e inicie la depuración (F5).  
  
5. En la instancia experimental, abra un proyecto. El VSPackage se cargará y se alcanzará el punto de interrupción.  
  
   Para especificar otros contextos en los que cargar su VSPackage, puede usar los campos de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Para obtener más información, vea [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>¿Cómo obtengo el objeto DTE?  
 Si el complemento no muestra una interfaz de usuario (por ejemplo, comandos de menú, botones de barra de herramientas o ventanas de herramienta) quizás pueda usar el código tal cual siempre que obtenga el objeto de automatización DTE del VSPackage. Le mostramos cómo:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Para obtener el objeto DTE de un VSPackage  
  
1. En un proyecto VSIX con una plantilla de elemento de paquete de Visual Studio, busque el <em>\<project name></em> archivo package.cs. Esta es la clase que deriva de <xref:Microsoft.VisualStudio.Shell.Package>; puede ayudarlo a interaccionar con Visual Studio. En este caso, usa su <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>.  
  
2. Agregue estas instrucciones `using`:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Busque el método `Initialize`. Este método controla el comando que especificó en el asistente para paquetes. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto DTE:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Cuando tenga el objeto de automatización <xref:EnvDTE.DTE>, puede agregar el resto del código de complemento al proyecto. Si necesita el objeto <xref:EnvDTE80.DTE2>, puede hacer lo mismo.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>¿Cómo cambio los comandos de menú y los botones de barra de herramientas en mi complemento al estilo de VSPackage?  
 Las extensiones VSPackage usan el archivo .vsct para crear la mayoría de los comandos de menú, barras de herramientas, botones de barra de herramientas y otras interfaces de usuario. La plantilla de elemento de proyecto de **comando personalizado** le ofrece la opción de crear un comando en el menú **herramientas** . Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información acerca de los archivos. Vsct, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Para ver tutoriales que muestran cómo usar el archivo. Vsct para agregar elementos de menú, barras de herramientas y botones de la barra de herramientas, vea [extender menús y comandos](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>¿Cómo agrego ventanas de herramienta personalizadas a la manera de VSPackage?  
 La plantilla de elemento de proyecto de la ventana de herramientas personalizada le ofrece la opción de crear una ventana de herramientas. Para obtener más información sobre esta plantilla de elemento de proyecto, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md). Para obtener información sobre las ventanas de herramientas, vea [extender y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md) y los artículos que hay bajo ella, especialmente [Agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>¿Cómo administro las ventanas de Visual Studio a la manera de VSPackage?  
 Si su complemento administra las ventanas de Visual Studio, el código de complemento debería funcionar en un VSPackage. Por ejemplo, este procedimiento muestra cómo agregar código que administra el **lista de tareas** al `MenuItemCallback` método del VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Para insertar código de administración de ventanas desde un complemento en un VSPackage  
  
1. Cree un VSPackage que tenga un comando de menú, como en la sección [Cómo empezar a desarrollar extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Abra el archivo que contiene la definición del VSPackage. (En un proyecto de C#, <em>\<your project name></em> es Package.cs).  
  
3. Agregue estas instrucciones `using`:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Busque el método `MenuItemCallback`. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Agregue el código de su complemento. Por ejemplo, este es un código que agrega nuevas tareas al **lista de tareas**, muestra el número de tareas y, a continuación, elimina una tarea.  
  
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
  
1. Cree un VSPackage que tenga un comando de menú, como en la sección [Cómo empezar a desarrollar extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Abra el archivo que contiene la definición del VSPackage. (En un proyecto de C#, <em>\<your project name></em> es Package.cs).  
  
3. Agregue estas instrucciones `using`:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Busque el método `MenuItemCallback`. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto <xref:EnvDTE80.DTE2>:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Agregue el código de su complemento. Por ejemplo, el siguiente código obtiene el nombre del proyecto de inicio en una solución. (Se debe abrir una solución multiproyecto cuando este paquete se ejecuta).  
  
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
