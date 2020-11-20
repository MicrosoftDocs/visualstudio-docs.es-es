---
title: Cambiar el texto de un comando de menú | Microsoft Docs
description: Obtenga información sobre cómo cambiar la etiqueta de texto de un comando de menú mediante el servicio IMenuCommandService. para ello, revise este ejemplo de código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d22669e67becb62d5e90f58c0cdd6b572e684bcf
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974395"
---
# <a name="change-the-text-of-a-menu-command"></a>Cambiar el texto de un comando de menú
En los pasos siguientes se muestra cómo cambiar la etiqueta de texto de un comando de menú mediante el <xref:System.ComponentModel.Design.IMenuCommandService> servicio.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Cambiar la etiqueta de un comando de menú con IMenuCommandService

1. Cree un proyecto VSIX denominado `MenuText` con un comando de menú llamado **ChangeMenuText**. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. En el archivo *. Vsct* , agregue la `TextChanges` marca al comando de menú, tal y como se muestra en el ejemplo siguiente.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. En el archivo *ChangeMenuText.CS* , cree un controlador de eventos al que se llamará antes de que se muestre el comando de menú.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    También puede actualizar el estado del comando de menú en este método cambiando las <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> propiedades, y <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> en el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto.

4. En el constructor ChangeMenuText, reemplace el código de inicialización y colocación del comando original por código que crea un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (en lugar de un `MenuCommand` ) que representa el comando de menú, agrega el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador de eventos y proporciona el comando de menú al servicio de comandos de menú.

    Este es el aspecto que debería tener:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

6. En el menú **herramientas** debería ver un comando llamado **Invoke ChangeMenuText**.

7. Haga clic en el comando. Debería ver el cuadro de mensaje que anuncia que se ha llamado a **MenuItemCallback** . Al descartar el cuadro de mensaje, debería ver que el nombre del comando en el menú herramientas es ahora **texto nuevo**.
