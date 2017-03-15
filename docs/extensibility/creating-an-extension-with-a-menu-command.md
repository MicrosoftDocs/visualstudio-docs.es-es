---
title: "Crear una extensi&#243;n con un comando de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "escribir un vspackage"
  - "VSPackage"
  - "tutoriales"
  - "paquete de Visual studio"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 56
---
# Crear una extensi&#243;n con un comando de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo crear una extensión con un comando de menú que inicia el Bloc de notas.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un comando de menú  
  
1.  Cree un proyecto VSIX denominado **FirstMenuCommand**. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de comando personalizado denominada **FirstCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **FirstCommand.cs**.  
  
3.  Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4.  En la instancia experimental, abra el  **Herramientas \/ extensiones y actualizaciones** ventana. Debería ver el **FirstMenuCommand** extensión aquí. \(Si abre **extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no podrá ver **FirstMenuCommand**\).  
  
     Ahora vaya a la **herramientas** menú en la instancia experimental. Debería ver **invocar FirstCommand** comando. En este punto, aparecerá un cuadro de mensaje que dice "FirstCommandPackage dentro de FirstMenuCommand.FirstCommand.MenuItemCallback\(\)". Veremos cómo iniciar realmente el Bloc de notas desde este comando en la sección siguiente.  
  
## Cambiar el controlador de comandos de menú  
 Ahora vamos a actualizar el controlador de comandos para iniciar el Bloc de notas.  
  
1.  Detener la depuración y volver a su instancia de trabajo de Visual Studio. Abra el archivo FirstCommand.cs y agregue la siguiente instrucción using:  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  Busque el constructor FirstCommand privado. Aquí es donde el comando está enlazado al servicio de comandos y se especifica el controlador de comandos. Cambie el nombre del controlador de comando para StartNotepad, de la manera siguiente:  
  
    ```c#  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Elimine el método MenuItemCallback y agregue un método StartNotepad que simplemente iniciará el Bloc de notas:  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Ahora, pruébela. Cuando empiece a depurar el proyecto y haga clic en **Herramientas \/ invocar FirstCommand**, debería ver una instancia del Bloc de notas que surjan.  
  
     Puede utilizar una instancia de la <xref:System.Diagnostics.Process> clase para ejecutar cualquier archivo ejecutable, no sólo el Bloc de notas. Pruébelo con calc.exe, por ejemplo.  
  
## Limpieza del entorno Experimental  
 Si está desarrollando varias extensiones o simplemente explorando resultados con distintas versiones de su código de extensión, su entorno experimental puede dejar de funcionar como debería. En este caso, debe ejecutar la secuencia de comandos de restablecimiento. Se llama **Restablecer la instancia Experimental de Visual Studio 2015**, y se distribuye como parte del SDK de Visual Studio. Esta secuencia de comandos quita todas las referencias a las extensiones desde el entorno experimental, para que pueda empezar desde cero.  
  
 Puede tener acceso a esta secuencia de comandos de dos maneras:  
  
1.  Desde el escritorio, busque **Restablecer la instancia Experimental de Visual Studio 2015**.  
  
2.  Desde la línea de comandos, ejecute lo siguiente:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## Implementar la extensión  
 Ahora que tiene la extensión de herramienta que se ejecuta como desee, ha llegado el momento de pensar en compartirla con sus amigos y compañeros. Es fácil, siempre que tienen instalado Visual Studio 2015. Todo lo que tiene que hacer es enviarles el archivo .vsix que ha creado. \(Asegúrese de crear en modo de lanzamiento\).  
  
 Puede encontrar el archivo .vsix para esta extensión en el directorio bin de FirstMenuCommand. En concreto, suponiendo que ha creado la configuración de lanzamiento, estará en:  
  
 **\< directorio de código \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 Para instalar la extensión, su amigo debe cerrar todas las instancias abiertas de Visual Studio, haga doble clic en el archivo .vsix, que muestra la **instalador VSIX**. Los archivos se copian en el **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** directory.  
  
 Cuando su amigo muestra vuelva a Visual Studio, encontrará la extensión FirstMenuCommand en **Herramientas \/ extensiones y actualizaciones**. Podrá ir a **extensiones y actualizaciones** para desinstalar o deshabilitar la extensión demasiado.  
  
## Pasos siguientes  
 Este tutorial le ha mostrado sólo una pequeña parte de lo que puede hacer con una extensión de Visual Studio. Presentamos una breve lista de cosas que puede hacer con las extensiones de Visual Studio \(razonablemente fáciles\):  
  
1.  Puede hacer muchas más cosas con un comando de menú simple:  
  
    1.  Agregue su propio icono: [Agregar iconos a los comandos de menú](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Cambiar el texto del comando de menú: [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Agregar un menú contextual a un comando: [Métodos abreviados de teclado de enlace a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Agregar distintos tipos de comandos, menús y barras de herramientas: [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)  
  
3.  Agregar ventanas de herramientas y extender las ventanas de herramientas integradas de Visual Studio: [Ampliación y personalización de ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Agregar IntelliSense, sugerencias de código y otras características a los editores de código: [Extender el Editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Agregar páginas de propiedades y opciones y configuración de usuario para la extensión: [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md) y [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)  
  
 Otros tipos de extensiones requieren un poco más de trabajo, como la creación de un nuevo tipo de proyecto \([Extender proyectos](../extensibility/extending-projects.md)\), crear un nuevo tipo de editor \([Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)\), o implementar la extensión de un shell aislado: [Shell de aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)