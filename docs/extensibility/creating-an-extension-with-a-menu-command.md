---
title: Creación de una extensión con un comando de menú ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739557"
---
# <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú

En este tutorial se muestra cómo crear una extensión con un comando de menú que inicia el Bloc de notas.

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-menu-command"></a>Crear un comando de menú

1. Cree un proyecto VSIX denominado **FirstMenuCommand**. Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada denominada **FirstCommand**. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione **Comando personalizado**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *FirstCommand.cs*.

3. Compile la solución y comience la depuración.

    Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [La instancia experimental](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. En la instancia experimental, abra la ventana**Extensiones y actualizaciones** de **herramientas.** >  Debería ver la extensión **FirstMenuCommand** aquí. (Si abre **Extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no verá **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. En la instancia experimental, abra la ventana **Extensions** > **Manage Extensions.** Debería ver la extensión **FirstMenuCommand** aquí. (Si abre **Administrar extensiones** en la instancia de trabajo de Visual Studio, no verá **FirstMenuCommand**).

::: moniker-end

Ahora vaya al menú **Herramientas** en la instancia experimental. Debería ver **Invocar comando FirstCommand.** En este punto, el comando muestra un cuadro de mensaje que dice **FirstCommandPackage Inside FirstMenuCommand.FirstCommand.MenuItemCallback()**. Veremos cómo iniciar realmente el Bloc de notas desde este comando en la siguiente sección.

## <a name="change-the-menu-command-handler"></a>Cambiar el controlador de comandos de menú

Ahora vamos a actualizar el controlador de comandos para iniciar el Bloc de notas.

1. Detenga la depuración y vuelva a la instancia de trabajo de Visual Studio. Abra el archivo *FirstCommand.cs* y agregue la siguiente instrucción using:

    ```csharp
    using System.Diagnostics;
    ```

2. Busque el constructor FirstCommand privado. Aquí es donde se enlaza el comando al servicio de comandos y se especifica el controlador de comandos. Cambie el nombre del controlador de comandos a StartNotepad, como se indica a continuación:

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

3. Quite `MenuItemCallback` el método `StartNotepad` y agregue un método, que simplemente iniciará el Bloc de notas:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Ahora pruébalo. Al iniciar la depuración del proyecto y hacer clic en **Herramientas** > **Invocar FirstCommand**, debería ver una instancia del Bloc de notas emergente.

    Puede utilizar una instancia <xref:System.Diagnostics.Process> de la clase para ejecutar cualquier ejecutable, no solo el Bloc de notas. Pruébalo con `calc.exe`, por ejemplo.

## <a name="clean-up-the-experimental-environment"></a>Limpiar el entorno experimental

Si está desarrollando varias extensiones o simplemente explorando resultados con diferentes versiones del código de extensión, su entorno experimental puede dejar de funcionar como debería. En este caso, debe ejecutar el script de restablecimiento. Se denomina **Restablecer la instancia experimental**de Visual Studio y se incluye como parte del SDK de Visual Studio. Este script elimina todas las referencias a las extensiones del entorno experimental, por lo que puede empezar desde cero.

Puede llegar a este script de una de estas dos maneras:

1. En el escritorio, busque **Restablecer la instancia experimental**de Visual Studio .

2. Ejecute lo siguiente desde la línea de comandos:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Implemente la extensión

Ahora que tienes tu extensión de herramienta funcionando como quieras, es hora de pensar en compartirla con tus amigos y colegas. Eso es fácil, siempre y cuando tengan Visual Studio 2015 instalado. Todo lo que tienes que hacer es enviarles el archivo *.vsix* que has creado. (Asegúrese de compilarlo en el modo de versión.)

Puede encontrar el archivo *.vsix* para esta extensión en el directorio bin *FirstMenuCommand.* Específicamente, suponiendo que usted ha construido la configuración de la versión, estará en:

*\<directorio de código>,FirstMenuCommand, FirstMenuCommand, bin, Release, FirstMenuCommand.vsix*

Para instalar la extensión, su amigo debe cerrar todas las instancias abiertas de Visual Studio y, a continuación, haga doble clic en el archivo *.vsix,* que abre el **instalador de VSIX**. Los archivos se copian en el *directorio %LocalAppData%-Microsoft-VisualStudio\<versión>-Extensions.*

Cuando tu amigo vuelva a aparecer Visual Studio, encontrará la extensión FirstMenuCommand en**Extensiones y actualizaciones**de **herramientas** > . Pueden ir a **Extensiones y actualizaciones** para desinstalar o deshabilitar la extensión, también.

## <a name="next-steps"></a>Pasos siguientes

Este tutorial le ha mostrado solo una pequeña parte de lo que puede hacer con una extensión de Visual Studio. Esta es una breve lista de otras cosas (razonablemente fáciles) que puede hacer con las extensiones de Visual Studio:

1. Puede hacer muchas más cosas con un simple comando de menú:

   1. Añadir su propio icono: [Añadir iconos a los comandos](../extensibility/adding-icons-to-menu-commands.md) de menú

   2. Cambiar el texto del comando de menú: [Cambiar el texto de un comando](../extensibility/changing-the-text-of-a-menu-command.md) de menú

   3. Añadir un acceso directo de menú a un comando: [Enlazar métodos abreviados](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) de teclado a elementos de menú

2. Añadir diferentes tipos de comandos, menús y barras de herramientas: [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)

3. Agregue ventanas de herramientas y amplíe las ventanas de herramientas integradas de Visual Studio: [Ampliar y personalizar ventanas](../extensibility/extending-and-customizing-tool-windows.md) de herramientas

4. Agregar IntelliSense, sugerencias de código y otras características a los editores de código existentes: [Amplíe el editor y](../extensibility/extending-the-editor-and-language-services.md) los servicios de lenguaje

5. Agregar opciones y páginas de propiedades y configuración de usuario a la extensión: [Extender propiedades y la ventana Propiedad](../extensibility/extending-properties-and-the-property-window.md) y Extender la configuración y las opciones de [usuario](../extensibility/extending-user-settings-and-options.md)

   Otros tipos de extensiones requieren un poco más de trabajo, como crear un nuevo tipo de proyecto ([Extender proyectos](../extensibility/extending-projects.md)), crear un nuevo tipo de editor ([Crear editores y diseñadores personalizados](../extensibility/creating-custom-editors-and-designers.md)) o implementar la extensión en un shell aislado: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de Visual Studio: Shell aislado de [Visual Studio: Shell aislado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/) de Visual Studio
