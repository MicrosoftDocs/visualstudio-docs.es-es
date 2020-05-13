---
title: Adición de un controlador de menú a una barra de herramientas . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740320"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Agregar un controlador de menú a una barra de herramientas
Este tutorial se basa en el agregar una barra de [herramientas a una ventana](../extensibility/adding-a-toolbar-to-a-tool-window.md) de herramientas tutorial y muestra cómo agregar un controlador de menú a la barra de herramientas de la ventana de herramientas. Los pasos que se muestran aquí también se pueden aplicar a la barra de herramientas que se crea en el tutorial Agregar una barra de [herramientas.](../extensibility/adding-a-toolbar.md)

Un controlador de menú es un control dividido. El lado izquierdo del controlador de menú muestra el último comando utilizado y puede ejecutarlo haciendo clic en él. El lado derecho del controlador de menú es una flecha que, al hacer clic, abre una lista de comandos adicionales. Al hacer clic en un comando de la lista, el comando se ejecuta y reemplaza el comando en el lado izquierdo del controlador de menú. De esta manera, el controlador de menú funciona como un botón de comando que siempre muestra el último comando utilizado de una lista.

Los controladores de menú pueden aparecer en los menús, pero se utilizan con mayor frecuencia en las barras de herramientas.

## <a name="prerequisites"></a>Prerrequisitos
A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-menu-controller"></a>Crear un controlador de menú

1. Siga los procedimientos descritos en Agregar una barra de [herramientas a una ventana](../extensibility/adding-a-toolbar-to-a-tool-window.md) de herramientas para crear una ventana de herramientas que tenga una barra de herramientas.

2. En *TWTestCommandPackage.vsct*, vaya a la sección Símbolos. En el guidSymbol elemento denominado **guidTWTestCommandPackageCmdSet**, declare el controlador de menú, grupo de controladores de menú y tres elementos de menú.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. En la sección Menús, después de la última entrada de menú, defina el controlador de menú como un menú.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Las `TextChanges` `TextIsAnchorCommand` marcas y deben incluirse para permitir que el controlador de menú refleje el último comando seleccionado.

4. En la sección Grupos, después de la última entrada de grupo, agregue el grupo de controladores de menú.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Al establecer el controlador de menú como el principal, los comandos colocados en este grupo aparecen en el controlador de menú. Se `priority` omite el atributo, que lo establece en el valor predeterminado de 0, porque es el único grupo en el controlador de menú.

5. En la sección Botones, después de la última entrada de botón, agregue un elemento Button para cada uno de los elementos de menú.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. En este punto, puede mirar el controlador de menú. Compile la solución y comience la depuración. Debería ver la instancia experimental.

   1. En el menú **Ver / Otras ventanas** , abra **Test ToolWindow**.

   2. El controlador de menú aparece en la barra de herramientas de la ventana de herramientas.

   3. Haga clic en la flecha en el lado derecho del controlador de menú para ver los tres comandos posibles.

      Tenga en cuenta que al hacer clic en un comando, el título del controlador de menú cambia para mostrar ese comando. En la siguiente sección, agregaremos el código para activar estos comandos.

## <a name="implement-the-menu-controller-commands"></a>Implementar los comandos del controlador de menú

1. En *TWTestCommandPackageGuids.cs*, agregue los iDE de comando para los tres elementos de menú después de los ides de comando existentes.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. En *TWTestCommand.cs*, agregue el siguiente `TWTestCommand` código en la parte superior de la clase.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. En el TWTestCommand constructor, después `AddCommand` de la última llamada al método, agregue código para enrutar los eventos de cada comando a través de los mismos controladores.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Agregue un controlador de eventos a la **clase TWTestCommand** para marcar el comando seleccionado como activado.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Agregue un controlador de eventos que muestre un cuadro de mensajes cuando el usuario seleccione un comando en el controlador de menú:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Probar el controlador de menú

1. Compile la solución y comience la depuración. Debería ver la instancia experimental.

2. Abra la ventana **Probar ToolWindow** en el menú **Ver / Otras ventanas.**

    El controlador de menú aparece en la barra de herramientas de la ventana de herramientas y muestra **EL elemento 1 de MC.**

3. Haga clic en el botón del controlador de menú a la izquierda de la flecha.

    Debería ver tres elementos, el primero de los cuales está seleccionado y tiene un cuadro de resaltado alrededor de su icono. Haga clic en **MC Elemento 3**.

    Aparece un cuadro de diálogo con el mensaje **Seleccionado Elemento 3**del controlador de menú . Observe que el mensaje corresponde al texto del botón del controlador de menú. El botón del controlador de menú ahora muestra **el elemento 3 de MC.**

## <a name="see-also"></a>Vea también
- [Adición de una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Adición de una barra de herramientas](../extensibility/adding-a-toolbar.md)
