---
title: "Cambiar la apariencia de un comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos, cambiar la apariencia"
  - "comandos de menú, cambiar la apariencia"
  - "menús, cambiar la apariencia de comando"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Cambiar la apariencia de un comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede proporcionar comentarios al usuario cambiando el aspecto de un comando. Por ejemplo, puede que un comando que parecen diferentes cuando no está disponible. Puede hacer que los comandos disponibles o no, ocultar o mostrar, o comprobar o anule su selección en el menú.  
  
 Para cambiar el aspecto de un comando, realice una de estas acciones:  
  
-   Especificar los marcadores apropiados en la definición de comando en el archivo de la tabla de comandos.  
  
-   Utilice el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.  
  
-   Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de la interfaz y modificar los objetos de comando sin procesar.  
  
 Los pasos siguientes muestran cómo buscar y actualizar el aspecto de un comando mediante el marco de paquete administrados \(MPF\).  
  
### Para cambiar la apariencia de un comando de menú  
  
1.  Siga las instrucciones de [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md) para crear un elemento de menú denominado `New Text`.  
  
2.  En el archivo ChangeMenuText.cs, agregue la siguiente instrucción using:  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  En el archivo ChangeMenuTextPackageGuids.cs, agregue la siguiente línea:  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  En el archivo ChangeMenuText.cs, reemplace el código en el método ShowMessageBox con lo siguiente:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obtener el comando que se va a actualizar desde la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> de objetos y, a continuación, establecer las propiedades adecuadas en el objeto de comando. Por ejemplo, el siguiente método hace que el comando especificado desde un comando de VSPackage conjunto disponible o no disponible. El código siguiente hace que el elemento de menú denominado `New Text` disponible después de que se ha hecho clic.  
  
    ```c#  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental de Visual Studio.  
  
7.  En el **herramientas** menú, haga clic en el **ChangeMenuText invocar** comando. En este punto es el nombre del comando **invocar ChangeMenuText**, por lo que el controlador de comandos no llama a ChangeMyCommand\(\).  
  
8.  En el **herramientas** ahora debería ver el menú **texto nuevo**. Haga clic en **texto nuevo**. Ahora se debe sombrear el comando.  
  
## Vea también  
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)