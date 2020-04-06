---
title: Cambio de la apariencia de un comando ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739852"
---
# <a name="change-the-appearance-of-a-command"></a>Cambiar la apariencia de un comando
Puede proporcionar comentarios al usuario cambiando la apariencia de un comando. Por ejemplo, es posible que desee que un comando tenga un aspecto diferente cuando no esté disponible. Puede hacer que los comandos estén disponibles o no disponibles, ocultarlos o mostrarlos, o marcarlos o desmarcarlos en el menú.

Para cambiar la apariencia de un comando, realice una de estas acciones:

- Especifique las marcas adecuadas en la definición de comando en el archivo de tabla de comandos.

- Utilice <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> el servicio.

- Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la interfaz y modifique los objetos de comando sin procesar.

  En los pasos siguientes se muestra cómo buscar y actualizar la apariencia de un comando mediante Managed Package Framework (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Para cambiar la apariencia de un comando de menú

1. Siga las instrucciones de [Cambiar el texto de un comando](../extensibility/changing-the-text-of-a-menu-command.md) de menú para crear un elemento de menú denominado `New Text`.

2. En el archivo *ChangeMenuText.cs,* agregue la siguiente instrucción using:

    ```csharp
    using System.Security.Permissions;
    ```

3. En el archivo *ChangeMenuTextPackageGuids.cs,* agregue la siguiente línea:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. En el *archivo ChangeMenuText.cs,* reemplace el código del método ShowMessageBox por lo siguiente:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Obtenga el comando que desea <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> actualizar desde el objeto y, a continuación, establezca las propiedades adecuadas en el objeto de comando. Por ejemplo, el método siguiente hace que el comando especificado de un conjunto de comandos de VSPackage esté disponible o no esté disponible. El código siguiente hace `New Text` que el elemento de menú denominado no esté disponible después de hacer clic en él.

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
        return cmdUpdated;
    }
    ```

6. Compile la solución y comience la depuración. Debería aparecer la instancia experimental de Visual Studio.

7. En el menú **Herramientas,** haga clic en el comando **Invocar ChangeMenuText.** En este punto, el nombre del comando es **Invoke ChangeMenuText**, por lo que el controlador de comandos no llama a **ChangeMyCommand()**.

8. En el menú **Herramientas** ahora debería ver **Nuevo texto**. Haga clic en **Nuevo texto**. El comando ahora debería estar atenuado.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Cómo VSPackages agregan elementos de interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Tabla de comandos de Visual Studio (. Vsct) Archivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
