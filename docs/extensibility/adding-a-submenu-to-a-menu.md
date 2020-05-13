---
title: Adición de un submenú a un menú de menú . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740272"
---
# <a name="add-a-submenu-to-a-menu"></a>Añadir un submenú a un menú
Este tutorial se basa en la demostración en Agregar un menú a la barra de [menús](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) de Visual Studio mostrando cómo agregar un submenú al menú **TestMenu.**

 Un submenú es un menú secundario que aparece en otro menú. Un submenú se puede identificar mediante la flecha que sigue a su nombre. Al hacer clic en el nombre, se mostrará el submenú y sus comandos.

 Este tutorial crea un submenú en un menú de la barra de menús de Visual Studio y coloca un nuevo comando en el submenú. El tutorial también implementa el nuevo comando.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="add-a-submenu-to-a-menu"></a>Añadir un submenú a un menú

1. Siga los pasos descritos en Agregar un menú a la barra de [menús](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) de Visual Studio para crear el proyecto y el elemento de menú. En los pasos de este tutorial se `TopLevelMenu`supone que el nombre del proyecto VSIX es .

2. Abra *TestCommandPackage.vsct*. En `<Symbols>` la sección, `<IDSymbol>` agregue un elemento para el submenú, uno para el grupo `<GuidSymbol>` de submenú y otro para el comando, todo en el nodo denominado "guidTopLevelMenuCmdSet." Este es el mismo nodo `<IDSymbol>` que contiene el elemento para el menú de nivel superior.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Agregue el submenú recién `<Menus>` creado a la sección.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     El par GUID/ID del elemento primario especifica el grupo de menús que se generó en Agregar un menú a la barra de [menús](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)de Visual Studio y es un elemento secundario del menú de nivel superior.

4. Agregue el grupo de menús `<Groups>` definido en el paso 2 a la sección y consitúe en un elemento secundario del submenú.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Agregue un `<Button>` nuevo `<Buttons>` elemento a la sección para definir el comando creado en el paso 2 como un elemento en el submenú.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Compile la solución y comience la depuración. Debería ver la instancia experimental.

7. Haga clic en **TestMenu** para ver un nuevo submenú denominado **Submenú**. Haga clic en **Submenú** para abrir el submenú y ver un nuevo comando, **Probar subcomando**. Observe que al hacer clic en **Probar subcomando** no hace nada.

## <a name="add-a-command"></a>Añadir un comando

1. Abra *TestCommand.cs* y agregue el siguiente ID de comando después del ID de comando existente.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Agregue el subcomando. Busque el constructor de comandos. Agregue las siguientes líneas justo `AddCommand` después de la llamada al método.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    El `SubItemCallback` controlador de comandos se definirá más adelante. El constructor ahora debería tener este aspecto:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Agregue `SubItemCallback()`. Este es el método al que se llama cuando se hace clic en el nuevo comando en el submenú.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

5. En el menú **TestMenu** , haga clic en **Submenú** y, a continuación, haga clic en **Probar subcomando**. Debe aparecer un cuadro de mensaje y mostrar el texto "Test Command Inside TestCommand.SubItemCallback()".

## <a name="see-also"></a>Vea también

- [Agregue un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
