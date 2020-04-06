---
title: Cambio del texto de un comando de menú ? Microsoft Docs
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
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739847"
---
# <a name="change-the-text-of-a-menu-command"></a>Cambiar el texto de un comando de menú
Los pasos siguientes muestran cómo cambiar la etiqueta <xref:System.ComponentModel.Design.IMenuCommandService> de texto de un comando de menú mediante el servicio.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Cambiar una etiqueta de comando de menú con el IMenuCommandService

1. Cree un proyecto `MenuText` VSIX denominado con un comando de menú denominado **ChangeMenuText**. Para obtener más información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. En el archivo *.vsct,* agregue la `TextChanges` marca al comando de menú, como se muestra en el ejemplo siguiente.

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

3. En el archivo *ChangeMenuText.cs,* cree un controlador de eventos al que se llamará antes de que se muestre el comando de menú.

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

    También puede actualizar el estado del comando de <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>menú <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>en <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> este <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> método cambiando las propiedades , , y en el objeto.

4. En el ChangeMenuText constructor, reemplace el código de inicialización y colocación de comandos original con código que crea un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (en lugar de un `MenuCommand`) que representa el comando de menú, agrega el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador de eventos y proporciona el comando de menú al servicio de comandos de menú.

    Esto es lo que debería parecer:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

6. En el menú **Herramientas** debería ver un comando denominado **Invocar ChangeMenuText**.

7. Haga clic en el comando. Debería ver el cuadro de mensaje que anuncia que **MenuItemCallback** se ha llamado. Al descartar el cuadro de mensaje, debería ver que el nombre del comando en el menú Herramientas ahora es **Nuevo texto**.
