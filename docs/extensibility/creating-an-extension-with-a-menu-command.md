---
title: "Crear una extensión con un comando de menú | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e9f72764d8fc87a9605f3bde20b7b2b93f44f39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú
Este tutorial muestra cómo crear una extensión con un comando de menú que se inicia el Bloc de notas.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Crear un comando de menú  
  
1.  Crear un proyecto VSIX denominado **FirstMenuCommand**. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de comando personalizado denominada **FirstCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **FirstCommand.cs**.  
  
3.  Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4.  En la instancia experimental, abra el **herramientas / extensiones y actualizaciones** ventana. Debería ver el **FirstMenuCommand** extensión aquí. (Si abre **extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no verá **FirstMenuCommand**).  
  
     Ahora, vaya a la **herramientas** menú en la instancia experimental. Debería ver **FirstCommand invocar** comando. En este momento, solo aparecerá un cuadro de mensaje que indicara "FirstCommandPackage dentro de FirstMenuCommand.FirstCommand.MenuItemCallback()". Veremos cómo inicia realmente el Bloc de notas de este comando en la sección siguiente.  
  
## <a name="changing-the-menu-command-handler"></a>Cambiar el controlador de comandos de menú  
 Ahora vamos a actualizar el controlador de comandos para iniciar el Bloc de notas.  
  
1.  Detener la depuración y volver a la instancia de trabajo de Visual Studio. Abra el archivo FirstCommand.cs y agregue la siguiente instrucción using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Busque el constructor FirstCommand privado. Aquí es donde el comando está enlazado al servicio de comandos y se especifica el controlador de comandos. Cambiar el nombre del controlador de comandos para StartNotepad, como se indica a continuación:  
  
    ```csharp  
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
  
3.  Quite el método MenuItemCallback y agregue un método StartNotepad que solo se iniciará el Bloc de notas:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Ahora, pruébela. Cuando empiece a depurar el proyecto y haga clic en **herramientas / invocar FirstCommand**, debería ver una instancia del Bloc de notas que surjan.  
  
     Puede usar una instancia de la <xref:System.Diagnostics.Process> clase para ejecutar archivos ejecutables, no solo el Bloc de notas. Pruébelo con calc.exe, por ejemplo.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Limpiar el entorno Experimental  
 Si está desarrollando varias extensiones, o simplemente explorar resultados con versiones diferentes de su código de extensión, el entorno experimental puede dejar de funcionar el aspecto que debería. En este caso, debe ejecutar la secuencia de comandos de restablecimiento. Se llama **restablecer la instancia Experimental de Visual Studio 2015**, y se distribuye como parte del SDK de Visual Studio. Esta secuencia de comandos quita todas las referencias a las extensiones desde el entorno experimental, para que pueda empezar desde cero.  
  
 Puede tener acceso a esta secuencia de comandos de dos maneras:  
  
1.  En el escritorio, buscar **restablecer la instancia Experimental de Visual Studio 2015**.  
  
2.  Desde la línea de comandos, ejecute lo siguiente:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Implementar la extensión  
 Ahora que tiene la extensión de la herramienta ejecuta la manera deseada, es el tiempo para pensar acerca de cómo compartir con amigos y compañeros de trabajo. Que es fácil, siempre y cuando tiene instalado Visual Studio 2015. Todo lo que tiene que hacer es les envíe el archivo .vsix que se compiló. (Asegúrese de crear en modo de lanzamiento).  
  
 Puede encontrar el archivo .vsix para esta extensión en el directorio de bin FirstMenuCommand. En concreto, suponiendo que ha creado la configuración de lanzamiento, estará en:  
  
 **\<directorio de código > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Para instalar la extensión, su amigo debe cerrar todas las instancias abiertas de Visual Studio y, después, haga doble clic en el archivo .vsix, que abrirá el **instalador VSIX**. Los archivos se copian en el **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** directory.  
  
 Cuando su amigo abre Visual Studio nuevo, encontrará la extensión FirstMenuCommand en **herramientas / extensiones y actualizaciones**. Puede ir a **extensiones y actualizaciones** para desinstalar o deshabilitar la extensión, demasiado.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Este tutorial le ha mostrado sólo una pequeña parte de lo que puede hacer con una extensión de Visual Studio. Esta es una lista breve de otras acciones (razonablemente fáciles) que puede realizar con extensiones de Visual Studio:  
  
1.  Puede hacer muchas más cosas con un comando de menú simple:  
  
    1.  Agregar su propio icono: [agregar iconos a los comandos de menú](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Cambiar el texto del comando de menú: [cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Agregar un menú contextual a un comando: [enlace métodos abreviados de teclado para elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Agregar distintos tipos de comandos, menús y barras de herramientas: [extender menús y comandos](../extensibility/extending-menus-and-commands.md)  
  
3.  Agregar ventanas de herramientas y ampliar las ventanas de herramientas integradas de Visual Studio: [ampliar y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Agregar sugerencias de código, IntelliSense y otras características existentes editores de código: [extender el Editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Agregar páginas de propiedades y opciones y configuración de usuario para la extensión: [extender las propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md) y [opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)  
  
 Otros tipos de extensiones requieren un poco más de trabajo, como la creación de un nuevo tipo de proyecto ([extender proyectos](../extensibility/extending-projects.md)), crear un nuevo tipo de editor ([crear editores personalizados y diseñadores](../extensibility/creating-custom-editors-and-designers.md)), o implementar la extensión en un shell aislado: [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)