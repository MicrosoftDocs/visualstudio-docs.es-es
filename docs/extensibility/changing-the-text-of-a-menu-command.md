---
title: "Cambiar el texto de un comando de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús, cambiar el texto"
  - "texto, menús"
  - "comandos de cambio de texto"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Cambiar el texto de un comando de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los pasos siguientes muestran cómo cambiar la etiqueta de texto de un comando de menú mediante el <xref:System.ComponentModel.Design.IMenuCommandService> service.  
  
## Cambiar una etiqueta de comando de menú con la interfaz  
  
1.  Cree un proyecto VSIX denominado `MenuText` con un comando de menú denominado **ChangeMenuText**. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  En el archivo .vstc, agregue el `TextChanges` marca a un comando de menú, como se muestra en el ejemplo siguiente.  
  
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
  
3.  En el archivo ChangeMenuText.cs, cree un controlador de eventos que se llama antes de que aparezca el comando de menú.  
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     También puede actualizar el estado del comando de menú en este método cambiando el <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, y <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> Propiedades en la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto.  
  
4.  En el constructor ChangeMenuText, reemplace el código de inicialización y la ubicación de comando original con código que crea un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(en lugar de un `MenuCommand`\) que representa el comando de menú, se agrega el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador de eventos y proporciona el menú de comandos para el servicio del comando de menú.  
  
     Aquí es lo que debería ser similar:  
  
    ```c#  
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
  
5.  Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
6.  En el **herramientas** menú verá un comando llamado **invocar ChangeMenuText**.  
  
7.  Haga clic en el comando. Debería ver el anuncio de cuadro de mensaje que se ha llamado MenuItemCallback. Al descartar el cuadro de mensaje, verá que el nombre del comando en el menú herramientas es ahora **texto nuevo**.