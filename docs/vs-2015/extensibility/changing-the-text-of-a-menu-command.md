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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072986"
---
# <a name="changing-the-text-of-a-menu-command"></a>Cambio del texto de un comando de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los pasos siguientes muestran cómo cambiar la etiqueta de texto de un comando de menú mediante el <xref:System.ComponentModel.Design.IMenuCommandService> service.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Cambiar una etiqueta de comando de menú con la interfaz  
  
1. Cree un proyecto VSIX denominado `MenuText` con un comando de menú denominado **ChangeMenuText**. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. En el archivo .vstc, agregue el `TextChanges` marca para el comando de menú, como se muestra en el ejemplo siguiente.  
  
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
  
3. En el archivo ChangeMenuText.cs, cree un controlador de eventos que se llamará antes de que se muestra el comando de menú.  
  
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
  
     También puede actualizar el estado del comando de menú en este método cambiando el <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, y <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> propiedades en el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto.  
  
4. En el constructor ChangeMenuText, reemplace el código de inicialización y la colocación de comandos original con el código que crea un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (en lugar de un `MenuCommand`) que representa el comando de menú, se agrega el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador de eventos y ofrece el menú comando para el servicio de comandos de menú.  
  
     Este es el aspecto debería:  
  
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
  
6. En el **herramientas** menú debería ver un comando llamado **ChangeMenuText invocar**.  
  
7. Haga clic en el comando. Debería ver el anuncio de cuadro de mensaje que se ha llamado MenuItemCallback. Al descartar el cuadro de mensaje, debería ver que ahora es el nombre del comando en el menú herramientas **nuevo texto**.
