---
title: Cambiar la apariencia de un comando | Microsoft Docs
description: Obtenga información sobre cómo proporcionar comentarios que cambien la apariencia de un comando, como hacer que los comandos estén disponibles o no disponibles, ocultos o mostrados o activados o desactivados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddeed08d7bc33b9a9ae5405876f3b28459d4eaf2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905038"
---
# <a name="change-the-appearance-of-a-command"></a>Cambiar la apariencia de un comando
Puede proporcionar comentarios al usuario cambiando la apariencia de un comando. Por ejemplo, puede que desee que un comando tenga un aspecto diferente cuando no esté disponible. Puede hacer que los comandos estén disponibles o no disponibles, ocultarlos o mostrarlos, o activarlos o desactivarlos en el menú.

Para cambiar la apariencia de un comando, realice una de estas acciones:

- Especifique las marcas adecuadas en la definición de comando en el archivo de tabla de comandos.

- Use el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> servicio .

- Implemente la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y modifique los objetos de comando sin formato.

  En los pasos siguientes se muestra cómo buscar y actualizar la apariencia de un comando mediante Managed Package Framework (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Para cambiar la apariencia de un comando de menú

1. Siga las instrucciones de [Cambiar el texto de un comando de menú para](../extensibility/changing-the-text-of-a-menu-command.md) crear un elemento de menú denominado `New Text` .

2. En el *archivo ChangeMenuText.cs,* agregue la siguiente instrucción using:

    ```csharp
    using System.Security.Permissions;
    ```

3. En el *archivo ChangeMenuTextPackageGuids.cs,* agregue la línea siguiente:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. En el *archivo ChangeMenuText.cs,* reemplace el código del método ShowMessageBox por lo siguiente:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Obtenga el comando que desea actualizar desde el objeto y, a <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> continuación, establezca las propiedades adecuadas en el objeto de comando. Por ejemplo, el método siguiente hace que el comando especificado de un conjunto de comandos de VSPackage esté disponible o no disponible. El código siguiente hace que el elemento de menú denominado `New Text` no esté disponible después de hacer clic en él.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. Compile la solución y comience la depuración. La instancia experimental de Visual Studio debe aparecer.

7. En el **menú Herramientas,** haga clic en **el comando Invocar ChangeMenuText.** En este momento, el nombre del comando es **Invoke ChangeMenuText**, por lo que el controlador de comandos no llama a **ChangeMyCommand().**

8. En el **menú** Herramientas, ahora debería ver **Nuevo texto.** Haga clic **en Nuevo texto.** Ahora, el comando debería estar atenuado.

## <a name="see-also"></a>Consulta también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Cómo agregan vsPackages elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Visual Studio tabla de comandos (. Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
