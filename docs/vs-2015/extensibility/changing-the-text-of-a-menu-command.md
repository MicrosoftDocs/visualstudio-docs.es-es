---
title: Cambiar el texto de un comando de menú | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184493"
---
# <a name="changing-the-text-of-a-menu-command"></a>Cambio del texto de un comando de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En los pasos siguientes se muestra cómo cambiar la etiqueta de texto de un comando de menú mediante el <xref:System.ComponentModel.Design.IMenuCommandService> servicio.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Cambiar la etiqueta de un comando de menú con IMenuCommandService  
  
1. Cree un proyecto VSIX denominado `MenuText` con un comando de menú llamado **ChangeMenuText**. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. En el archivo. vstc, agregue la `TextChanges` marca al comando de menú, tal y como se muestra en el ejemplo siguiente.  
  
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
  
3. En el archivo ChangeMenuText.cs, cree un controlador de eventos al que se llamará antes de que se muestre el comando de menú.  
  
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
  
6. En el menú **herramientas** debería ver un comando llamado **Invoke ChangeMenuText**.  
  
7. Haga clic en el comando. Debería ver el cuadro de mensaje que anuncia que se ha llamado a MenuItemCallback. Al descartar el cuadro de mensaje, debería ver que el nombre del comando en el menú herramientas es ahora **texto nuevo**.
