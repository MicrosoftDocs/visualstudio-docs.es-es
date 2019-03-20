---
title: Creación de una extensión con un comando de menú | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e8e98a20fafc825af0cf9486c8a9939c02e3b5f
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194527"
---
# <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú

Este tutorial muestra cómo crear una extensión con un comando de menú que se inicia el Bloc de notas.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Crear un comando de menú

1. Cree un proyecto VSIX denominado **FirstMenuCommand**. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** diálogo buscando "vsix".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizado denominada **FirstCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C#** > **extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para *FirstCommand.cs*.

3. Compile la solución y comience la depuración.

    Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [la instancia experimental](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. En la instancia experimental, abra el **herramientas** > **extensiones y actualizaciones** ventana. Debería ver el **FirstMenuCommand** extensión aquí. (Si abre **extensiones y actualizaciones** en su instancia de trabajo de Visual Studio, no verá **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. En la instancia experimental, abra el **extensiones** > **administrar extensiones** ventana. Debería ver el **FirstMenuCommand** extensión aquí. (Si abre **administrar extensiones** en su instancia de trabajo de Visual Studio, no verá **FirstMenuCommand**).

::: moniker-end

Ahora, vaya a la **herramientas** menú en la instancia experimental. Debería ver **FirstCommand invocar** comando. En este momento, el comando aparece un cuadro de mensaje que dice **FirstCommandPackage dentro de FirstMenuCommand.FirstCommand.MenuItemCallback()**. Veremos cómo se inicia realmente el Bloc de notas desde este comando en la sección siguiente.

## <a name="change-the-menu-command-handler"></a>Cambiar el controlador de comandos de menú

Ahora vamos a actualizar el controlador de comandos para iniciar el Bloc de notas.

1. Detener la depuración y vuelva a su instancia de trabajo de Visual Studio. Abra el *FirstCommand.cs* de archivo y agregue la siguiente instrucción using:

    ```csharp
    using System.Diagnostics;
    ```

2. Busque el constructor FirstCommand privado. Aquí es donde el comando está enlazado al servicio de comandos y se especifica el controlador de comandos. Cambiar el nombre del controlador de comandos para StartNotepad, como se indica a continuación:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Quitar el `MenuItemCallback` método y agregue un `StartNotepad` método, que solo se iniciará el Bloc de notas:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Ahora, pruébela. Cuando empiece a depurar el proyecto y haga clic en **herramientas** > **FirstCommand invocar**, debería ver una instancia del Bloc de notas que aparezcan.

    Puede usar una instancia de la <xref:System.Diagnostics.Process> clase para ejecutar cualquier archivo ejecutable, no solo el Bloc de notas. Pruébelo con `calc.exe`, por ejemplo.

## <a name="clean-up-the-experimental-environment"></a>Limpiar el entorno experimental

Si está desarrollando varias extensiones o simplemente explorando resultados con distintas versiones del código de extensión, el entorno experimental puede dejar de funcionar como debería. En este caso, debe ejecutar el script de restablecimiento. Se llama **restablecer la instancia Experimental de Visual Studio**, y se proporciona como parte del SDK de Visual Studio. Esta secuencia de comandos quita todas las referencias a las extensiones desde el entorno experimental, para que pueda empezar desde cero.

Puede tener acceso a esta secuencia de comandos de dos maneras:

1. Desde el escritorio, busque **restablecer la instancia Experimental de Visual Studio**.

2. Ejecute lo siguiente desde la línea de comandos:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Implementar la extensión

Ahora que tiene la extensión de herramienta que se ejecuta como quiera, es momento de pensar en compartirla con amigos y compañeros de trabajo. Es fácil, siempre tengan instalado Visual Studio 2015. Lo único que debe hacer es enviarles el *.vsix* generó el archivo. (Asegúrese de compilarlo en modo de lanzamiento).

Puede encontrar el *.vsix* archivo para esta extensión en el *FirstMenuCommand* directorio bin. En concreto, suponiendo que ha creado la configuración de Release, estará en:

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

Para instalar la extensión, su amigo debe cerrar todas las instancias abiertas de Visual Studio y, después, haga doble clic en el *.vsix* archivo, que abre el **instalador de VSIX**. Los archivos se copian en el *%LocalAppData%\Microsoft\VisualStudio\<versión > \Extensions* directory.

Cuando su amigo abre vuelva a Visual Studio, encontrará la extensión FirstMenuCommand en **herramientas** > **extensiones y actualizaciones**. Pueden ir a **extensiones y actualizaciones** para desinstalar o deshabilitar la extensión, demasiado.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha mostrado solo una pequeña parte de lo que puede hacer con una extensión de Visual Studio. Esta es una breve lista de las cosas (razonablemente fáciles) que puede hacer con extensiones de Visual Studio:

1. Puede hacer muchas más cosas con un comando de menú simple:

   1. Agregue su propio icono: [Agregar iconos a comandos de menú](../extensibility/adding-icons-to-menu-commands.md)

   2. Cambiar el texto del comando de menú: [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Agregar un menú contextual a un comando: [Enlazar métodos abreviados de teclado a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Agregar distintos tipos de comandos, menús y barras de herramientas: [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md)

3. Agregar ventanas de herramientas y extender las ventanas de herramientas integradas de Visual Studio: [Ampliar y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)

4. Agregar IntelliSense, las sugerencias de código y otras características de los editores de código existentes: [Ampliar los servicios de editor y lenguaje](../extensibility/extending-the-editor-and-language-services.md)

5. Agregar páginas de propiedades y las opciones y configuración de usuario para la extensión: [Extender las propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md) y [ampliar las opciones y configuración de usuario](../extensibility/extending-user-settings-and-options.md)

   Otros tipos de extensiones requieren un poco más de trabajo, como la creación de un nuevo tipo de proyecto ([ampliar proyectos](../extensibility/extending-projects.md)), crear un nuevo tipo de editor ([crear editores personalizados y diseñadores](../extensibility/creating-custom-editors-and-designers.md)), o implementando la extensión en un shell aislado: [Shell de Visual Studio aislado](/visualstudio/extensibility/shell/visual-studio-isolated-shell)
