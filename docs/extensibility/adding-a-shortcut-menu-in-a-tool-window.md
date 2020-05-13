---
title: Adición de un menú contextual en una ventana de herramientas . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740279"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Añadir un menú contextual en una ventana de herramientas
Este tutorial coloca un menú contextual en una ventana de herramientas. Un menú contextual es un menú contextual que aparece cuando un usuario hace clic con el botón derecho en un botón, cuadro de texto o fondo de ventana. Los comandos de un menú contextual se comportan igual que los comandos de otros menús o barras de herramientas. Para admitir un menú contextual, estibre en el archivo *.vsct* y muéselo en respuesta al clic derecho del ratón.

Una ventana de herramientas consta de un control de usuario <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>WPFWPF en una clase de ventana de herramientas personalizada que hereda de .

En este tutorial se muestra cómo crear un menú contextual como un menú de Visual Studio, declarando elementos de menú en el archivo *.vsct* y, a continuación, mediante Managed Package Framework para implementarlos en la clase que define la ventana de herramientas. Este enfoque facilita el acceso a los comandos de Visual Studio, los elementos de interfaz de usuario y el modelo de objetos de automatización.

Como alternativa, si el menú contextual no tendrá acceso <xref:System.Windows.FrameworkElement.ContextMenu%2A> a la funcionalidad de Visual Studio, puede usar la propiedad de un elemento XAML en el control de usuario. Para obtener más información, vea [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Prerrequisitos
A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-the-tool-window-shortcut-menu-package"></a>Cree el paquete de menú contextual de la ventana de herramientas

1. Cree un proyecto `TWShortcutMenu` VSIX con el nombre y agregue una plantilla de ventana de herramientas denominada **ShortcutMenu.** Para obtener más información sobre cómo crear una ventana de herramientas, consulte Crear una extensión con una ventana de [herramientas.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="specifying-the-shortcut-menu"></a>Especificar el menú contextual
Un menú contextual como el que se muestra en este tutorial permite al usuario seleccionar de una lista de colores que se utilizan para rellenar el fondo de la ventana de herramientas.

1. En *ShortcutMenuPackage.vsct*, busque en el guidSymbol elemento denominado guidShortcutMenuPackageCmdSety declare el menú contextual, el grupo de menúcontextual y las opciones de menú. El guidsymbol elemento ahora debe tener este aspecto:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Justo antes del elemento Buttons, cree un elemento Menus y, a continuación, defina el menú contextual en él.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Un menú contextual no tiene un elemento primario porque no forma parte de un menú o barra de herramientas.

3. Cree un elemento Groups con un elemento Group que contenga los elementos de menú contextual y asocie el grupo al menú contextual.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. En el elemento Botones, defina los comandos individuales que aparecerán en el menú contextual. El elemento Buttons debe tener este aspecto:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. En *ShortcutMenuCommand.cs*, agregue las definiciones para el GUID del conjunto de comandos, el menú contextual y los elementos de menú.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Estos son los mismos iDs de comando que se definen en la sección Símbolos del archivo *ShortcutMenuPackage.vsct.* El grupo de contexto no se incluye aquí porque solo es necesario en el archivo *.vsct.*

## <a name="implementing-the-shortcut-menu"></a>Implementación del menú contextual
 Esta sección implementa el menú contextual y sus comandos.

1. En *ShortcutMenu.cs*, la ventana de herramientas puede obtener el servicio de comandos de menú, pero el control que contiene no puede. Los pasos siguientes muestran cómo hacer que el servicio de comandos de menú esté disponible para el control de usuario.

2. En *ShortcutMenu.cs*, agregue las siguientes directivas using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Invalide el método Initialize() de la ventana de herramientas para obtener el servicio de comandos de menú y agregar el control, pasando el servicio de comandos de menú al constructor:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. En el constructor de la ventana de la herramienta ShortcutMenu, quite la línea que agrega el control. El constructor ahora debería tener este aspecto:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. En *ShortcutMenuControl.xaml.cs*, agregue un campo privado para el servicio de comandos de menú y cambie el constructor de control para tomar el servicio de comandos de menú. A continuación, utilice el servicio de comandos de menú para agregar los comandos de menú contextual. El ShortcutMenuControl constructor ahora debe parecerse al código siguiente. El controlador de comandos se definirá más adelante.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. En *ShortcutMenuControl.xaml*, <xref:System.Windows.UIElement.MouseRightButtonDown> agregue un <xref:System.Windows.Controls.UserControl> evento al elemento de nivel superior. El archivo XAML ahora debería tener este aspecto:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. En *ShortcutMenuControl.xaml.cs*, agregue un código auxiliar para el controlador de eventos.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Agregue las siguientes directivas using al mismo archivo:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implemente `MyToolWindowMouseRightButtonDown` el evento de la siguiente manera.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Esto crea <xref:System.ComponentModel.Design.CommandID> un objeto para el menú contextual, identifica la ubicación del clic del <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> mouse y abre el menú contextual en esa ubicación mediante el método.

10. Implemente el controlador de comandos.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    En este caso, solo un método controla los <xref:System.ComponentModel.Design.CommandID> eventos de todos los elementos de menú identificando el y estableciendo el color de fondo en consecuencia. Si los elementos de menú hubieran contenido comandos no relacionados, habría creado un controlador de eventos independiente para cada comando.

## <a name="test-the-tool-window-features"></a>Pruebe las características de la ventana de herramientas

1. Compile la solución y comience la depuración. Aparece la instancia experimental.

2. En la instancia experimental, haga clic en **Ver / Otras ventanas**y, a continuación, haga clic en **Menú acceso directo**. Esto debería mostrar la ventana de herramientas.

3. Haga clic con el botón derecho en el cuerpo de la ventana de herramientas. Se debe mostrar un menú contextual que tenga una lista de colores.

4. Haga clic en un color en el menú contextual. El color de fondo de la ventana de herramientas debe cambiarse al color seleccionado.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Uso y prestación de servicios](../extensibility/using-and-providing-services.md)
