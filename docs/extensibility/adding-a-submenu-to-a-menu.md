---
title: Agregar un submenú a un menú | Microsoft Docs
description: Obtenga información sobre cómo crear un submenú, agregarlo a la barra de menús de Visual Studio y agregar un nuevo comando al submenú.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 16b58a6ab6a01ff635b3afd58b06133abacf970e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598021"
---
# <a name="add-a-submenu-to-a-menu"></a>Agregar un submenú a un menú
Este tutorial se basa en la demostración de [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) mostrando cómo agregar un submenú al menú **TestMenu** .

 Un submenú es un menú secundario que aparece en otro menú. Un submenú se puede identificar mediante la flecha que sigue a su nombre. Al hacer clic en el nombre, se muestran el submenú y sus comandos.

 En este tutorial se crea un submenú en un menú de la barra de menús de Visual Studio y se coloca un nuevo comando en el submenú. En el tutorial también se implementa el nuevo comando.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Agregar un submenú a un menú

1. Siga los pasos descritos en [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) para crear el proyecto y el elemento de menú. En los pasos de este tutorial se supone que el nombre del Proyecto VSIX es `TopLevelMenu` .

2. Abra *TestCommandPackage. Vsct*. En la `<Symbols>` sección, agregue un `<IDSymbol>` elemento para el submenú, uno para el grupo de submenú y otro para el comando, todos en el `<GuidSymbol>` nodo denominado "guidTopLevelMenuCmdSet". Es el mismo nodo que contiene el `<IDSymbol>` elemento para el menú de nivel superior.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Agregue el submenú recién creado a la `<Menus>` sección.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     El par GUID/identificador del elemento primario especifica el grupo de menús que se generó en [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)y es un elemento secundario del menú de nivel superior.

4. Agregue el grupo de menús definido en el paso 2 a la `<Groups>` sección y conviértalo en un elemento secundario del submenú.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Agregue un nuevo `<Button>` elemento a la `<Buttons>` sección para definir el comando creado en el paso 2 como un elemento en el submenú.

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

7. Haga clic en **TestMenu** para ver un nuevo submenú denominado **submenú**. Haga clic en **submenú** para abrir el submenú y ver un nuevo comando, **Test sub Command**. Tenga en cuenta que al hacer clic en **subcomando de prueba** no se realiza ninguna acción.

## <a name="add-a-command"></a>Agregar un comando

1. Abra *TestCommand.CS* y agregue el siguiente identificador de comando después del identificador de comando existente.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Agregue el subcomando. Busque el constructor de comandos. Agregue las siguientes líneas justo después de la llamada al `AddCommand` método.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    El `SubItemCallback` controlador de comandos se definirá más adelante. El constructor debería tener ahora el siguiente aspecto:

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

3. Agregue `SubItemCallback()`. Este es el método al que se llama cuando se hace clic en el nuevo comando del submenú.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
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

5. En el menú **TestMenu** , haga clic en **submenú** y, a continuación, haga clic en **probar subcomando**. Debe aparecer un cuadro de mensaje y mostrar el texto "comando de prueba dentro de prueba. SubItemCallback ()".

## <a name="see-also"></a>Consulte también

- [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
