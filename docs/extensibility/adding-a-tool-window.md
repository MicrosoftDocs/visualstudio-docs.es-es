---
title: Adición de una ventana de herramientas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5ffcc334a69a38da4869532d633960cfac7260d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317138"
---
# <a name="add-a-tool-window"></a>Agregar una ventana de herramientas
En este tutorial aprenderá a crear una ventana de herramientas e integrarla en Visual Studio de las maneras siguientes:

- Agregar un control a la ventana de herramientas.

- Agregar una barra de herramientas a una ventana de herramientas.

- Agregar un comando a la barra de herramientas.

- Implemente los comandos.

- Establezca la posición predeterminada para la ventana de herramientas.

## <a name="prerequisites"></a>Requisitos previos
A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Crear una ventana de herramientas

1. Cree un proyecto denominado **FirstToolWin** con la plantilla VSIX y agrega una plantilla de elemento de ventana de herramienta personalizada denominada **FirstToolWindow**.

    > [!NOTE]
    > Para obtener más información acerca de cómo crear una extensión con una ventana de herramientas, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Agregar un control a la ventana de herramientas

1. Quite el control predeterminado. Abra *FirstToolWindowControl.xaml* y elimine el **Click Me!** .

2. En el **cuadro de herramientas**, expanda el **todos los controles de WPF** sección y arrastre el **elemento multimedia** el control a la **FirstToolWindowControl** formulario. Seleccione el control y en el **propiedades** ventana, el nombre de este elemento **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Agregar una barra de herramientas a la ventana de herramientas
Mediante la adición de una barra de herramientas de la siguiente manera, se garantiza que su degradados y los colores son coherentes con el resto del IDE.

1. En **el Explorador de soluciones**, abra *FirstToolWindowPackage.vsct*. El *.vsct* archivo define los elementos de interfaz gráfica de usuario en la ventana de herramientas mediante el uso de XML.

2. En el `<Symbols>` sección, busque la `<GuidSymbol>` nodo cuyo `name` atributo es `guidFirstToolWindowPackageCmdSet`. Agregue las dos siguientes `<IDSymbol>` elementos a la lista de `<IDSymbol>` elementos en este nodo para definir un barra de herramientas y un grupo de la barra de herramientas.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Justo encima el `<Buttons>` , debe crearse un `<Menus>` sección que se parezca a esto:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Hay varios tipos de menú. Este menú es una barra de herramientas en una ventana de herramientas definida por su `type` atributo. El `guid` y `id` valores componen el identificador completo de la barra de herramientas. Normalmente, el `<Parent>` de un menú es el grupo que lo contiene. Sin embargo, una barra de herramientas se define como su elemento primario. Por lo tanto, se usa el mismo identificador para el `<Menu>` y `<Parent>` elementos. El `priority` atributo es simplemente "0".

4. Las barras de herramientas son similares a los menús de muchas maneras. Por ejemplo, igual que un menú puede tener grupos de comandos, barras de herramientas también pueden tener grupos. (En los menús, los grupos de comandos se separan con líneas horizontales. En las barras de herramientas, los grupos no están separados por visuales divisores.)

    Agregar un `<Groups>` sección que contiene un `<Group>` elemento. Esto define el grupo cuyo Id. declarado en el `<Symbols>` sección. Agregar el `<Groups>` sección justo después del `<Menus>` sección.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Al establecer al elemento primario GUID e ID en el GUID y el identificador de la barra de herramientas, agregue el grupo a la barra de herramientas.

## <a name="add-a-command-to-the-toolbar"></a>Agregar un comando a la barra de herramientas
 Agregar un comando a la barra de herramientas que se muestra como un botón.

1. En la `<Symbols>` sección, declare los siguientes elementos IDSymbol justo después de la barra de herramientas y la barra de herramientas de declaraciones de grupo.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Agregar un elemento de botón dentro de la `<Buttons>` sección. Este elemento aparecerá en la barra de herramientas en la ventana de herramientas, con un **búsqueda** icono (Lupa).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Abra *FirstToolWindowCommand.cs* y agregue las líneas siguientes en la clase justo después de los campos existentes.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Así, los comandos disponibles en el código.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Agregar una propiedad de MediaPlayer a FirstToolWindowControl
Desde los controladores de eventos para los controles de barra de herramientas, el código debe poder tener acceso al control de Reproductor multimedia, que es un elemento secundario de la clase FirstToolWindowControl.

En **el Explorador de soluciones**, haga clic en *FirstToolWindowControl.xaml*, haga clic en **ver código**y agregue el código siguiente a la clase FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Crear una instancia de la ventana de herramientas y la barra de herramientas
Agregar una barra de herramientas y un comando de menú que invoca la **abrir archivo** cuadro de diálogo y se reproduce el archivo multimedia seleccionado.

1. Abra *FirstToolWindow.cs* y agregue la siguiente `using` instrucciones.

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Dentro de la clase FirstToolWindow, agregue una referencia al control FirstToolWindowControl pública.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Al final del constructor, establezca esta variable de control para el control recién creado.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Crear una instancia de la barra de herramientas dentro del constructor.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. En este momento el constructor FirstToolWindow este aspecto:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Agregar el comando de menú a la barra de herramientas. En la clase FirstToolWindowCommand.cs, agregue la siguiente instrucción using

    ```csharp
    using System.Windows.Forms;
    ```

7. En la clase FirstToolWindowCommand, agregue el código siguiente al final del método ShowToolWindow(). El controlador de botón comando se implementará en la sección siguiente.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Para implementar un comando de menú en la ventana de herramientas

1. En la clase FirstToolWindowCommand, agregue un método de controlador de botón que invoca la **abrir archivo** cuadro de diálogo. Cuando se ha seleccionado un archivo, reproduce el archivo multimedia.

2. En la clase FirstToolWindowCommand, agregue una referencia a la ventana FirstToolWindow que se crea en el método FindToolWindow() privada.

    ```csharp
    private FirstToolWindow window;
    ```

3. Cambiar el método ShowToolWindow() para establecer la ventana definida anteriormente (de modo que el controlador de comandos del controlador de botón puede tener acceso al control de ventana. Este es el método ShowToolWindow() completo.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Agregue el método de controlador de botón. Crea un componente OpenFileDialog para el usuario especificar el archivo multimedia para reproducir, y, después, reproduce el archivo seleccionado.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Establecer la posición predeterminada para la ventana de herramientas
 A continuación, especifique una ubicación predeterminada en el IDE para la ventana de herramientas. Información de configuración de la ventana de herramientas se encuentra en la *FirstToolWindowPackage.cs* archivo.

1. En *FirstToolWindowPackage.cs*, busque el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atributo el `FirstToolWindowPackage` (clase), que pasa el tipo de FirstToolWindow al constructor. Para especificar una posición de forma predeterminada, debe agregar más parámetros al constructor de ejemplo siguiente.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    El primer parámetro con nombre es `Style` y su valor es `Tabbed`, lo que significa que la ventana será una pestaña en una ventana existente. La posición de acoplamiento especificada por el `Window` parámetro, n este caso, el GUID de la **el Explorador de soluciones**.

    > [!NOTE]
    > Para obtener más información sobre los tipos de ventanas en el IDE, vea <xref:EnvDTE.vsWindowType>.

## <a name="test-the-tool-window"></a>Probar la ventana de herramientas

1. Presione **F5** para abrir una nueva instancia de la compilación experimental de Visual Studio.

2. En el **vista** menú, elija **Other Windows** y, a continuación, haga clic en **primera ventana de herramientas**.

    Debe abrir la ventana de herramientas del Reproductor de medios en la misma posición que **el Explorador de soluciones**. Si sigue apareciendo en la misma posición que antes, restablecer el diseño de ventana (**ventana / Restablecer diseño de ventana**).

3. Haga clic en el botón (tiene el **búsqueda** icono) en la ventana de herramientas. Seleccione un sonido compatible o un archivo de vídeo, por ejemplo, *C:\windows\media\chimes.wav*, a continuación, presione **abierto**.

    Debe escuchar la campanada.

## <a name="see-also"></a>Vea también
[Los comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
