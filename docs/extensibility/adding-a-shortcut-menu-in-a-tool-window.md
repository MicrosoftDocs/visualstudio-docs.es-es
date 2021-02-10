---
title: Agregar un menú contextual en una ventana de herramientas | Microsoft Docs
description: Obtenga información sobre cómo agregar un menú contextual a una ventana de herramientas en Visual Studio que aparece cuando se hace clic con el botón derecho en un botón, un cuadro de texto o un fondo de ventana.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a35652c0eacf22a46eed3f3fc64c3bcc0d6d10ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951542"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Agregar un menú contextual en una ventana de herramientas
En este tutorial se coloca un menú contextual en una ventana de herramientas. Un menú contextual es un menú que aparece cuando un usuario hace clic con el botón secundario en un botón, un cuadro de texto o un fondo de la ventana. Los comandos de un menú contextual se comportan igual que los comandos de otros menús o barras de herramientas. Para admitir un menú contextual, especifíquelo en el archivo *. Vsct* y mostrarlo como respuesta al clic con el botón secundario del mouse.

Una ventana de herramientas está formada por un control de usuario de WPF en una clase de ventana de herramientas personalizada que hereda de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

En este tutorial se muestra cómo crear un menú contextual como un menú de Visual Studio, declarando los elementos de menú en el archivo *. Vsct* y usando el marco de trabajo del paquete administrado para implementarlos en la clase que define la ventana de herramientas. Este enfoque facilita el acceso a los comandos de Visual Studio, los elementos de la interfaz de usuario y el modelo de objetos de automatización.

Como alternativa, si el menú contextual no va a tener acceso a la funcionalidad de Visual Studio, puede usar la <xref:System.Windows.FrameworkElement.ContextMenu%2A> propiedad de un elemento XAML en el control de usuario. Para obtener más información, vea [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Requisitos previos
A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Crear el paquete del menú contextual de la ventana de herramientas

1. Cree un proyecto VSIX denominado `TWShortcutMenu` y agregue una plantilla de ventana de herramientas denominada **MenúDeMétodoAbreviado** a él. Para obtener más información sobre cómo crear una ventana de herramientas, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Especificar el menú contextual
Un menú contextual como el que se muestra en este tutorial permite al usuario seleccionar en una lista de colores que se usan para rellenar el fondo de la ventana de herramientas.

1. En *ShortcutMenuPackage. Vsct*, busque en el elemento GuidSymbol denominado guidShortcutMenuPackageCmdSet y declare el menú contextual, el grupo de menús contextuales y las opciones de menú. El elemento GuidSymbol debe tener ahora el siguiente aspecto:

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

2. Justo antes del elemento Buttons, cree un elemento menus y, a continuación, defina el menú contextual en él.

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

    Un menú contextual no tiene un elemento primario porque no forma parte de un menú o una barra de herramientas.

3. Cree un elemento Groups con un elemento Group que contenga los elementos de menú contextual y asocie el grupo con el menú contextual.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. En el elemento botones, defina los comandos individuales que aparecerán en el menú contextual. El elemento botones debe tener el siguiente aspecto:

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

5. En *ShortcutMenuCommand.CS*, agregue las definiciones para el GUID del conjunto de comandos, el menú contextual y los elementos de menú.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Estos son los mismos identificadores de comando que se definen en la sección Symbols del archivo *ShortcutMenuPackage. Vsct* . El grupo de contexto no se incluye aquí porque solo es necesario en el archivo *. Vsct* .

## <a name="implementing-the-shortcut-menu"></a>Implementación del menú contextual
 En esta sección se implementa el menú contextual y sus comandos.

1. En *ShortcutMenu.CS*, la ventana de herramientas puede obtener el servicio de comandos de menú, pero el control que contiene no puede. En los pasos siguientes se muestra cómo hacer que el servicio de comandos de menú esté disponible para el control de usuario.

2. En *ShortcutMenu.CS*, agregue las siguientes directivas Using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Invalide el método Initialize () de la ventana de herramientas para obtener el servicio de comandos de menú y agregar el control, pasando el servicio de comandos de menú al constructor:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. En el constructor de la ventana de herramientas de ShortcutMenu, quite la línea que agrega el control. El constructor debería tener ahora el siguiente aspecto:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. En *ShortcutMenuControl.Xaml.CS*, agregue un campo privado para el servicio de comandos de menú y cambie el constructor del control para que tome el servicio de comandos de menú. A continuación, use el servicio de comandos de menú para agregar los comandos del menú contextual. El constructor ShortcutMenuControl debe ser ahora similar al código siguiente. El controlador de comandos se definirá más adelante.

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

6. En *ShortcutMenuControl. Xaml*, agregue un <xref:System.Windows.UIElement.MouseRightButtonDown> evento al elemento de nivel superior <xref:System.Windows.Controls.UserControl> . El archivo XAML debería tener el siguiente aspecto:

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

7. En *ShortcutMenuControl.Xaml.CS*, agregue un código auxiliar para el controlador de eventos.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
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

9. Implemente el `MyToolWindowMouseRightButtonDown` evento como se indica a continuación.

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

    <xref:System.ComponentModel.Design.CommandID>De este modo se crea un objeto para el menú contextual, se identifica la ubicación del clic del mouse y se abre el menú contextual en esa ubicación mediante el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> método.

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

    En este caso, solo un método controla eventos para todos los elementos de menú mediante la identificación de <xref:System.ComponentModel.Design.CommandID> y el establecimiento del color de fondo en consecuencia. Si los elementos de menú tenían comandos no relacionados, habría creado un controlador de eventos independiente para cada comando.

## <a name="test-the-tool-window-features"></a>Probar las características de la ventana de herramientas

1. Compile la solución y comience la depuración. Aparece la instancia experimental.

2. En la instancia experimental, haga clic en **Ver/otras ventanas** y, a continuación, haga clic en **MenúDeMétodoAbreviado**. Esto debería mostrar la ventana de herramientas.

3. Haga clic con el botón secundario en el cuerpo de la ventana de herramientas. Se debe mostrar un menú contextual con una lista de colores.

4. Haga clic en un color en el menú contextual. El color de fondo de la ventana de herramientas debe cambiarse al color seleccionado.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Uso y suministro de servicios](../extensibility/using-and-providing-services.md)
