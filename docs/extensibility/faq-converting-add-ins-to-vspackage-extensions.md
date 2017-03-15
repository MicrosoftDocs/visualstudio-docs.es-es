---
title: "Preguntas m&#225;s frecuentes: Convertir complementos en extensiones de VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Preguntas m&#225;s frecuentes: Convertir complementos en extensiones de VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Complementos están desusados. Para realizar una nueva extensión de Visual Studio, debe crear una extensión VSIX. Aquí están las respuestas a algunas preguntas frecuentes acerca de cómo convertir un complemento de Visual Studio en una extensión VSIX.  
  
> [!WARNING]
>  A partir de Visual Studio 2015, para los proyectos de C\# y Visual Basic, puede usar el proyecto VSIX y agregar plantillas de elemento para los comandos de menú, ventanas de herramientas y VSPackages. Para obtener más información, consulta [Novedades en el SDK Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  En muchos casos, simplemente puede transferir el código de complemento a un proyecto VSIX con un elemento de proyecto de VSPackage. Puede obtener el objeto de automatización DTE mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> en la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(método\).  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Para obtener más información, consulte [¿Cómo se puede ejecutar el código del complemento en un VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) a continuación.  
  
## ¿Qué software es necesario desarrollar extensiones VSIX?  
 Extensiones de Visual Studio requieren el SDK de Visual Studio 2015, además de Visual Studio 2015.  Cuando cree un proyecto VSIX o abrir un proyecto VSIX existente, Visual Studio descarga el software necesario. Para obtener más información acerca de cómo instalar el SDK de Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## ¿Dónde está la documentación de extensión?  
 Comience con [Empezando a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Otros artículos sobre el desarrollo de extensión VSSDK en MSDN están por debajo de ésta.  
  
## ¿Puedo convertir mi proyecto de complemento a un proyecto VSIX?  
 No se puede convertir un proyecto directamente a un proyecto VSIX porque los mecanismos utilizados en proyectos VSIX no son iguales que las de los proyectos de complemento. La plantilla de proyecto VSIX, además de las plantillas de elemento de proyecto tienen una gran cantidad de código que resulta relativamente fácil de configurar y en ejecución como una extensión VSIX.  
  
##  <a name="BKMK_StartDeveloping"></a> ¿Cómo se puede iniciar el desarrollo de las extensiones VSIX?  
 Le mostramos cómo realizar una extensión VSIX que contiene un comando de menú:  
  
#### Para hacer una extensión VSIX que tiene un comando de menú  
  
1.  Crear un proyecto de VSIX. \(**Archivo**, **nuevo**, **proyecto**, o tipo **proyecto** en el **Inicio rápido** ventana\). En el **nuevo proyecto** diálogo cuadro, expanda **Visual C\# \/ extensibilidad** o **Visual Basic \/ extensibilidad** y seleccione **proyecto VSIX**.\) Denomine el proyecto **TestExtension** y especifique una ubicación para él.  
  
2.  Agregar un **comando personalizado** plantilla de elemento de proyecto. \(Haga clic en el nodo del proyecto en el **el Explorador de soluciones** y seleccione **Agregar \/ nuevo elemento**. En el **nuevo proyecto** cuadro de diálogo de Visual C\# o Visual Basic, seleccione el **extensibilidad** nodo y seleccione **comando personalizado**.\)  
  
3.  Presione F5 para compilar y ejecutar el proyecto en modo de depuración.  
  
     Aparece una segunda instancia de Visual Studio. Esta segunda instancia se denomina la instancia experimental, y no puede tener la misma configuración que la instancia de Visual Studio que se utiliza para escribir código. La primera vez que ejecuta la instancia experimental, deberá iniciar sesión en VS Online y especifique el tema y el perfil.  
  
     En el **herramientas** menú \(en la instancia experimental\) verá un botón denominado **My Command name**. Al elegir este botón, debe aparecer un mensaje: **dentro de Testvspackagepackage.MenuItemCallback**.  
  
##  <a name="BKMK_RunAddin"></a> ¿Cómo se puede ejecutar el código del complemento en un VSPackage?  
 Código de complemento normalmente se ejecuta en uno de dos maneras:  
  
-   Desencadena un comando de menú \(el código está en el `IDTCommandTarget.Exec` método\)  
  
-   En el inicio \(el código está en el `OnConnection` controlador de eventos.\)  
  
 Puede hacer lo mismo en un VSPackage. Aquí se muestra cómo agregar código de complemento en el método de devolución de llamada:  
  
#### Implementar un comando de menú en un VSPackage  
  
1.  Crear un VSPackage que tenga un comando de menú. \(Para obtener más información, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)\).  
  
2.  Abra el archivo que contiene la definición del VSPackage. \(En un proyecto de C\#, tiene *\< NombreDeProyecto \>*Package.cs.\)  
  
3.  Agregue las siguientes `using` instrucciones al archivo:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Buscar el `MenuItemCallback` método. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener la <xref:EnvDTE80.DTE2> objeto:  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Agregue el código que el complemento en su `IDTCommandTarget.Exec` método. Por ejemplo, aquí es un código que agrega un nuevo panel a la **salida** ventana e imprime "Some Text" en el panel nuevo.  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Compilar y ejecutar este proyecto. Presione F5 o seleccione **iniciar** en el **Depurar** barra de herramientas. En la instancia experimental de Visual Studio, el **herramientas** menú debe tener un botón denominado **My Command name**. Al elegir este botón, las palabras **Some Text** debe aparecer en una **salida** panel de ventana. \(Es posible que deba abrir el **salida** ventana.\)  
  
 También puede tener el código se ejecute en el inicio. Sin embargo, este enfoque es generalmente se desaconseja para las extensiones de VSPackage. Si hay demasiadas extensiones intenta cargar cuando se inicia Visual Studio, la hora de inicio será notablemente mayor. Es una mejor práctica cargar el VSPackage automáticamente solo cuando se cumple alguna condición \(por ejemplo, una solución que se va a abrir\).  
  
 Este procedimiento muestra cómo ejecutar código de complemento en un VSPackage que se carga automáticamente cuando se abre una solución:  
  
#### Para cargar automáticamente un VSPackage  
  
1.  Cree un proyecto VSIX con un elemento de proyecto del paquete de Visual Studio. \(Para que los pasos para hacerlo, consulte [¿Cómo se puede iniciar el desarrollo de las extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Simplemente agregue el **paquete de Visual Studio** de elementos de proyecto en su lugar.\) Denomine el proyecto VSIX **nombre TestAutoload**.  
  
2.  Abra TestAutoloadPackage.cs. Busque la línea donde se declara la clase de paquete:  
  
    ```c#  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Encima de esta línea es un conjunto de atributos. Agregue este atributo:  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Establecer un punto de interrupción en el `Initialize()` método e inicie la depuración \(F5\).  
  
5.  En la instancia experimental, abra un proyecto. El VSPackage se cargará y se alcanzará el punto de interrupción.  
  
 Puede especificar otros contextos en los que se va a cargar su VSPackage mediante los campos de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Para obtener más información, consulta [Cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## ¿Cómo se puede obtener el objeto DTE?  
 Si el complemento no mostrar interfaz de usuario, por ejemplo, comandos de menú, botones de barra de herramientas o ventanas de herramientas, es posible que pueda usar el código como\-es siempre que obtenga el objeto de automatización DTE del VSPackage. Le mostramos cómo:  
  
#### Para obtener el objeto DTE de un VSPackage  
  
1.  En un proyecto VSIX con una plantilla de elementos de paquete de Visual Studio, busque el *\< nombre proyecto \>*archivo Package.cs. Esta es la clase que deriva de <xref:Microsoft.VisualStudio.Shell.Package>; puede ayudarle a interactuar con Visual Studio. En este caso, utilice su <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener la <xref:EnvDTE80.DTE2> objeto.  
  
2.  Agregue estas `using` instrucciones:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Buscar el `Initialize` método. Este método controla el comando especificado en el Asistente para paquetes. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener el objeto DTE:  
  
    ```c#  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Una vez que la <xref:EnvDTE.DTE> objeto de automatización, puede agregar el resto del código de complemento al proyecto. Si necesita la <xref:EnvDTE80.DTE2> del objeto, puede hacer lo mismo.  
  
## ¿Cómo cambio los comandos de menú y botones de barra de herramientas en mi complemento al estilo de VSPackage?  
 Extensiones de VSPackage utilizan el archivo .vsct para crear la mayoría de los comandos de menú, barras de herramientas, botones de barra de herramientas y otras interfaces de usuario. El **comando personalizado** plantilla de elemento de proyecto le ofrece la opción de crear un comando en el **herramientas** menú. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información acerca de los archivos .vsct, vea [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Para ver tutoriales que muestran cómo utilizar el archivo .vsct para agregar elementos de menú, barras de herramientas y botones de barra de herramientas, consulte [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md).  
  
## ¿Cómo agrego ventanas de herramientas personalizadas de la manera de VSPackage?  
 La plantilla de elemento de proyecto de ventana de herramientas personalizada proporciona la opción para crear una ventana de herramientas. Para obtener más información acerca de esta plantilla de elemento de proyecto, vea [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md). Para obtener información acerca de las ventanas de herramienta, consulte [Ampliación y personalización de ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md) y los artículos, especialmente [Agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
## ¿Cómo se administran las ventanas de Visual Studio en la manera de VSPackage?  
 Si su complemento administra windows de Visual Studio, el código debería funcionar en un VSPackage. Por ejemplo, este procedimiento muestra cómo agregar código que administra el **lista de tareas** a la `MenuItemCallback` método de VSPackage.  
  
#### Para insertar el código de administración de ventanas de un complemento en un VSPackage  
  
1.  Cree un VSPackage que tenga un comando de menú, como en la [¿Cómo se puede iniciar el desarrollo de las extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sección.  
  
2.  Abra el archivo que contiene la definición del VSPackage. \(En un proyecto de C\#, tiene *\< NombreDeProyecto \>*Package.cs.\)  
  
3.  Agregue estas `using` instrucciones:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Buscar el `MenuItemCallback` método. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener la <xref:EnvDTE80.DTE2> objeto:  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Agregue el código del complemento. Por ejemplo, aquí es un código que agrega nuevas tareas a la **lista de tareas**, indica el número de tareas y, a continuación, se elimina una tarea.  
  
    ```c#  
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
  
## ¿Cómo administro proyectos y soluciones en un VSPackage?  
 Si su complemento administra proyectos y soluciones, el código debería funcionar en un VSPackage. Por ejemplo, este procedimiento muestra cómo agregar código que obtiene el proyecto de inicio.  
  
1.  Cree un VSPackage que tenga un comando de menú, como en la [¿Cómo se puede iniciar el desarrollo de las extensiones VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sección.  
  
2.  Abra el archivo que contiene la definición del VSPackage. \(En un proyecto de C\#, tiene *\< NombreDeProyecto \>*Package.cs.\)  
  
3.  Agregue estas `using` instrucciones:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Buscar el `MenuItemCallback` método. Agregue una llamada a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener la <xref:EnvDTE80.DTE2> objeto:  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Agregue el código del complemento. Por ejemplo, el código siguiente obtiene el nombre del proyecto de inicio en una solución. \(Una solución de varios proyecto debe estar abierta cuando se ejecuta este paquete.\)  
  
    ```c#  
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
  
## ¿Cómo se puede establecer métodos abreviados de teclado en un VSPackage?  
 Utiliza el `<KeyBindings>` elemento del archivo vsct. En el ejemplo siguiente, el método abreviado de teclado para el comando `idCommand1` es ALT\+a y el método abreviado de teclado para el comando `idCommand2` es Ctrl \+ Alt \+ A. Observe la sintaxis de los nombres de clave.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## ¿Cómo se puede controlar eventos de automatización en un VSPackage?  
 Controlar eventos de automatización en un VSPackage del mismo modo que en el complemento. El código siguiente muestra cómo controlar la `OnItemRenamed` eventos. \(En este ejemplo se supone que ya ha obtenido el objeto DTE.\)  
  
```c#  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```