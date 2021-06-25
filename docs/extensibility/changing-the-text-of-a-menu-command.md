---
title: Cambiar el texto de un comando de menú | Microsoft Docs
description: Obtenga información sobre cómo cambiar la etiqueta de texto de un comando de menú mediante el servicio IMenuCommandService revisando este ejemplo de código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 541acf1bcf448541fe6c440eb2aada687cfbe0e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904996"
---
# <a name="change-the-text-of-a-menu-command"></a>Cambiar el texto de un comando de menú
Los pasos siguientes muestran cómo cambiar la etiqueta de texto de un comando de menú mediante el <xref:System.ComponentModel.Design.IMenuCommandService> servicio .

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Cambio de una etiqueta de comando de menú con IMenuCommandService

1. Cree un proyecto VSIX denominado `MenuText` con un comando de menú denominado **ChangeMenuText.** Para obtener más información, vea [Crear una extensión con un comando de menú.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. En el *archivo .vsct,* agregue `TextChanges` la marca al comando de menú, como se muestra en el ejemplo siguiente.

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

3. En el *archivo ChangeMenuText.cs,* cree un controlador de eventos al que se llamará antes de que se muestre el comando de menú.

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

    También puede actualizar el estado del comando de menú en este método cambiando las propiedades <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> , y del objeto <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .

4. En el constructor ChangeMenuText, reemplace el código original de inicialización y colocación de comandos por código que crea (en lugar de ) que representa el comando de menú, agrega el controlador de eventos y proporciona el comando de menú al servicio de comandos de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> `MenuCommand` <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> menú.

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

6. En el **menú** Herramientas debería ver un comando denominado **Invoke ChangeMenuText**.

7. Haga clic en el comando . Debería ver el cuadro de mensaje que anuncia que se ha llamado **a MenuItemCallback.** Al descartar el cuadro de mensaje, debería ver que el nombre del comando en el menú Herramientas ahora es **Nuevo texto.**
