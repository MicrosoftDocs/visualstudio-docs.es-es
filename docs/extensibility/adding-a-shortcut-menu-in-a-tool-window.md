---
title: "Agregar un menú contextual en una ventana de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ab921bec73528be7207baebdf9cb31885e2253fd
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Agregar un menú contextual en una ventana de herramientas
En este tutorial, se coloca un menú contextual en una ventana de herramientas. Un acceso directo es un menú que aparece cuando un usuario seleccione un botón, el cuadro de texto o el fondo de la ventana. Comandos de un menú contextual comportan igual que los comandos de otros menús o barras de herramientas. Para admitir un menú contextual, especifique en el archivo .vsct y mostrar en respuesta a la con el botón secundario del mouse.  
  
 Una ventana de herramientas consta de un control de usuario WPF en una clase de ventana de herramientas personalizada que hereda de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
 Este tutorial muestra cómo crear un menú contextual como un menú de Visual Studio, declarar elementos de menú en el archivo .vsct y, a continuación, utilizando Managed Package Framework implementarlos en la clase que define la ventana de herramientas. Este enfoque facilita el acceso a comandos de Visual Studio, los elementos de interfaz de usuario y el modelo de objetos de automatización.  
  
 Como alternativa, si el menú contextual no tendrán acceso a la funcionalidad de Visual Studio, puede utilizar el <xref:System.Windows.FrameworkElement.ContextMenu%2A>propiedad de un elemento XAML en el control de usuario.</xref:System.Windows.FrameworkElement.ContextMenu%2A> Para obtener más información, consulte [ContextMenu](http://msdn.microsoft.com/Library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Crear el paquete de menú de acceso directo de ventana de herramienta  
  
1.  Cree un proyecto VSIX denominado `TWShortcutMenu` y agregue una plantilla de la ventana de herramienta denominada **menú contextual** a él. Para obtener más información acerca de cómo crear una ventana de herramientas, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Especificar el menú contextual  
 Un menú contextual, como se muestra en este tutorial permite al usuario seleccionar de una lista de colores que se usan para rellenar el fondo de la ventana de herramientas.  
  
1.  En ShortcutMenuPackage.vsct, busque en el elemento de GuidSymbol denominado guidShortcutMenuPackageCmdSet y declare el menú contextual, grupo de menú de accesos directos y opciones de menú. El elemento GuidSymbol debe tener el siguiente aspecto:  
  
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
  
2.  Justo antes del elemento de botones, cree un elemento de menús y, a continuación, defina el menú contextual en él.  
  
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
  
3.  Cree un elemento de grupos con un elemento de grupo que contiene los elementos de menú contextual y asociar el grupo con el menú contextual.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  En el elemento de botones, definir los comandos individuales que aparecerán en el menú contextual. El elemento de botones debe tener este aspecto:  
  
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
  
5.  En ShortcutMenuPackageGuids.cs, agregue que las definiciones para el comando establecen GUID, el menú contextual y los elementos de menú.  
  
    ```c#  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Estos son los mismos identificadores de comando que se definen en la sección de símbolos del archivo ShortcutMenuPackage.vsct. El grupo de contexto no se incluye aquí porque es necesaria sólo en el archivo .vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementar el acceso directo  
 En esta sección se implementa el menú contextual y sus comandos.  
  
1.  En ShortcutMenu.cs, la ventana de herramientas puede obtener el servicio del comando de menú, pero no el control que contiene. Los pasos siguientes muestran cómo hacer que el servicio de comandos de menú disponibles para el control de usuario.  
  
2.  En ShortcutMenu.cs, agregue las siguientes instrucciones using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Invalide el método Initialize() de la ventana de herramienta para obtener el servicio del comando de menú y agregar el control, pasar al servicio de comando de menú para el constructor:  
  
    ```c#  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  En el constructor de ventana de herramienta de menú contextual, quite la línea que se agrega el control. El constructor debe tener el siguiente aspecto:  
  
    ```c#  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  En ShortcutMenuControl.xaml.cs, agregue un campo privado para el servicio del comando de menú y cambie el constructor del control para aprovechar el servicio de comandos de menú. A continuación, utilice el servicio del comando de menú para agregar los comandos del menú contextual. El constructor ShortcutMenuControl debe ser ahora similar al código siguiente. El controlador de comandos se definirán más adelante.  
  
    ```c#  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  En ShortcutMenuControl.xaml, agregue un <xref:System.Windows.UIElement.MouseRightButtonDown>evento al nivel superior <xref:System.Windows.Controls.UserControl>elemento.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.UIElement.MouseRightButtonDown> El archivo XAML debe ser ahora similar al siguiente:  
  
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
  
7.  En ShortcutMenuControl.xaml.cs, agregue un código auxiliar para el controlador de eventos.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Agregue las siguientes instrucciones using al mismo archivo:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implemente el `MyToolWindowMouseRightButtonDown` eventos como sigue.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Esto crea un <xref:System.ComponentModel.Design.CommandID>objeto para el menú contextual, identifica la ubicación del clic del mouse y se abre el menú contextual en esa ubicación mediante el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>método.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> </xref:System.ComponentModel.Design.CommandID>  
  
10. Implementar el controlador de comandos.  
  
    ```c#  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     En este caso, un solo método controla los eventos de todos los elementos de menú mediante la identificación de la <xref:System.ComponentModel.Design.CommandID>y estableciendo el color de fondo en consecuencia.</xref:System.ComponentModel.Design.CommandID> Si los elementos de menú contenía comandos no relacionados, habría creado un controlador de eventos independiente para cada comando.  
  
## <a name="testing-the-tool-window-features"></a>Probar las características de la ventana de herramienta  
  
1.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
2.  En la instancia experimental, haga clic en **vista y otras ventanas**y, a continuación, haga clic en **menú contextual**. Esto debe mostrar la ventana de herramientas.  
  
3.  Haga clic en el cuerpo de la ventana de herramientas. Debe mostrarse un menú contextual con una lista de colores.  
  
4.  Haga clic en un color en el menú contextual. El color de fondo de la ventana de herramienta debe cambiarse al color seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)
