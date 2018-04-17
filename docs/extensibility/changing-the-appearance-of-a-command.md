---
title: Cambiar la apariencia de un comando | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a19793f16991bc61636a929822757823728a926
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-appearance-of-a-command"></a>Cambiar la apariencia de un comando
Puede proporcionar comentarios al usuario cambiando la apariencia de un comando. Por ejemplo, puede que desee un comando que parecen diferentes cuando no está disponible. Puede hacer que los comandos disponibles o no está disponible, ocultar o mostrar, o comprobar o anule su selección en el menú.  
  
 Para cambiar la apariencia de un comando, realice una de estas acciones:  
  
-   Especifica las marcas adecuadas en la definición de comando en el archivo de la tabla de comandos.  
  
-   Use el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.  
  
-   Implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de interfaz y modificar los objetos de comando sin formato.  
  
 Los pasos siguientes muestran cómo buscar y actualizar la apariencia de un comando mediante Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Para cambiar la apariencia de un comando de menú  
  
1.  Siga las instrucciones de [cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md) para crear un elemento de menú denominado `New Text`.  
  
2.  En el archivo ChangeMenuText.cs, agregue la siguiente instrucción using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  En el archivo ChangeMenuTextPackageGuids.cs, agregue la siguiente línea:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  En el archivo ChangeMenuText.cs, reemplace el código en el método ShowMessageBox con lo siguiente:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obtener el comando que desea actualizar desde la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> de objeto y, a continuación, establecer las propiedades adecuadas en el objeto de comando. Por ejemplo, el método siguiente hace que el comando especificado desde un comando de VSPackage conjunto disponible o no está disponible. El código siguiente hace que el elemento de menú denominado `New Text` no está disponible después de que se ha hecho clic.  
  
    ```csharp  
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
  
7.  En el **herramientas** menú, haga clic en el **ChangeMenuText invocar** comando. En este punto es el nombre del comando **ChangeMenuText invocar**, por lo que el controlador de comandos no llama a ChangeMyCommand().  
  
8.  En el **herramientas** menú ahora debería ver **nuevo texto**. Haga clic en **nuevo texto**. El comando debe ahora atenuado.  
  
## <a name="see-also"></a>Vea también  
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)   
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)