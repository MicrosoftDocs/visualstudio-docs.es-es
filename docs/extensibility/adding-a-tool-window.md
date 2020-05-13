---
title: Adición de una ventana de herramientas ( Tool Window) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740255"
---
# <a name="add-a-tool-window"></a>Añadir una ventana de herramientas

En este tutorial aprenderá a crear una ventana de herramientas e integrarla en Visual Studio de las siguientes maneras:

- Agregue un control a la ventana de herramientas.

- Agregue una barra de herramientas a una ventana de herramientas.

- Agregue un comando a la barra de herramientas.

- Implemente los comandos.

- Establezca la posición predeterminada para la ventana de herramientas.

## <a name="prerequisites"></a>Prerrequisitos

El SDK de Visual Studio se incluye como una característica opcional en la instalación de Visual Studio. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-tool-window"></a>Crear una ventana de herramientas

1. Cree un proyecto denominado **FirstToolWin** con la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **FirstToolWindow**.

    > [!NOTE]
    > Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, consulte [Crear una extensión con una ventana](../extensibility/creating-an-extension-with-a-tool-window.md)de herramientas .

## <a name="add-a-control-to-the-tool-window"></a>Añadir un control a la ventana de herramientas

1. Quite el control predeterminado. Abra *FirstToolWindowControl.xaml* y elimine **el Click Me!** .

2. En el cuadro de **herramientas**, expanda el **todos los controles WPFWPF** sección y arrastre el **elemento multimedia** control a la **FirstToolWindowControl** formulario. Seleccione el control y, en la ventana **Propiedades,** asigne a este elemento el nombre **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Agregue una barra de herramientas a la ventana de herramientas
Al agregar una barra de herramientas de la siguiente manera, garantiza que sus degradados y colores son coherentes con el resto del IDE.

1. En **el Explorador**de soluciones , abra *FirstToolWindowPackage.vsct*. El archivo *.vsct* define los elementos de la interfaz gráfica de usuario (GUI) en la ventana de herramientas mediante XML.

2. En `<Symbols>` la sección, `<GuidSymbol>` busque `name` el `guidFirstToolWindowPackageCmdSet`nodo cuyo atributo es . Agregue los `<IDSymbol>` dos elementos `<IDSymbol>` siguientes a la lista de elementos de este nodo para definir una barra de herramientas y un grupo de barras de herramientas.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Justo encima de `<Buttons>` `<Menus>` la sección, cree una sección que se asemeje a esto:

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

    Hay varios tipos diferentes de menú. Este menú es una barra de herramientas `type` en una ventana de herramientas, definida por su atributo. La `guid` `id` configuración y la configuración componen el ID completo de la barra de herramientas. Normalmente, `<Parent>` el de un menú es el grupo contenedor. Sin embargo, una barra de herramientas se define como su propio elemento primario. Por lo tanto, se `<Menu>` utiliza `<Parent>` el mismo identificador para los elementos y. El `priority` atributo es simplemente '0'.

4. Las barras de herramientas se asemejan a los menús de muchas maneras. Por ejemplo, al igual que un menú puede tener grupos de comandos, las barras de herramientas también pueden tener grupos. (En los menús, los grupos de comandos están separados por líneas horizontales. En las barras de herramientas, los grupos no están separados por divisores visuales.)

    Agregue `<Groups>` una sección `<Group>` que contenga un elemento. Esto define el grupo cuyo `<Symbols>` identificador declaró en la sección. Agregue `<Groups>` la sección `<Menus>` justo después de la sección.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Al establecer el GUID principal y el identificador en el GUID y el identificador de la barra de herramientas, agregue el grupo a la barra de herramientas.

## <a name="add-a-command-to-the-toolbar"></a>Agregue un comando a la barra de herramientas

Agregue un comando a la barra de herramientas, que se muestra como un botón.

1. En `<Symbols>` la sección, declare los siguientes elementos IDSymbol justo después de las declaraciones de grupo de barra de herramientas y barra de herramientas.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Agregue un elemento `<Buttons>` Button dentro de la sección. Este elemento aparecerá en la barra de herramientas en la ventana de herramientas, con un icono **de búsqueda** (lupa).

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

3. Abra *FirstToolWindowCommand.cs* y agregue las siguientes líneas en la clase justo después de los campos existentes.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Esto hace que los comandos estén disponibles en el código.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Agregue una propiedad MediaPlayer a FirstToolWindowControl
Desde los controladores de eventos para los controles de barra de herramientas, el código debe ser capaz de tener acceso a la Media Player control, que es un elemento secundario de la FirstToolWindowControl clase.

En **el Explorador**de soluciones , haga clic con el botón secundario en *FirstToolWindowControl.xaml*, haga clic en Ver **código**y agregue el código siguiente a la clase FirstToolWindowControl .

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Crear una instancia de la ventana de herramientas y la barra de herramientas
Agregue una barra de herramientas y un comando de menú que invoque el cuadro de diálogo **Abrir archivo** y reproduzca el archivo multimedia seleccionado.

1. Abra *FirstToolWindow.cs* y `using` agregue las siguientes directivas:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Dentro de la FirstToolWindow clase, agregue una referencia pública a la FirstToolWindowControl control.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Al final del constructor, establezca esta variable de control en el control recién creado.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Cree una instancia de la barra de herramientas dentro del constructor.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. En este punto, el FirstToolWindow constructor debe tener este aspecto:

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

6. Agregue el comando de menú a la barra de herramientas. En la clase FirstToolWindowCommand.cs, agregue la siguiente directiva using:

    ```csharp
    using System.Windows.Forms;
    ```

7. En la clase FirstToolWindowCommand, agregue el código siguiente al final del método ShowToolWindow(). El comando ButtonHandler se implementará en la siguiente sección.

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

1. En la clase FirstToolWindowCommand, agregue un método ButtonHandler que invoque el cuadro de diálogo **Abrir archivo.** Cuando se ha seleccionado un archivo, reproduce el archivo multimedia.

2. En la clase FirstToolWindowCommand, agregue una referencia privada a la ventana FirstToolWindow que se crea en el método FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Cambie el método ShowToolWindow() para establecer la ventana que definió anteriormente (para que el controlador de comandos ButtonHandler pueda tener acceso al control de ventana. Aquí está el método showToolWindow() completo.

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

4. Agregue el Método ButtonHandler. Crea un OpenFileDialog para que el usuario especifique el archivo multimedia que se va a reproducir y, a continuación, reproduce el archivo seleccionado.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Establezca la posición predeterminada para la ventana de herramientas

A continuación, especifique una ubicación predeterminada en el IDE para la ventana de herramientas. La información de configuración de la ventana de herramientas se encuentra en el archivo *FirstToolWindowPackage.cs.*

1. En *FirstToolWindowPackage.cs*, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> busque `FirstToolWindowPackage` el atributo de la clase, que pasa el tipo FirstToolWindow al constructor. Para especificar una posición predeterminada, debe agregar más parámetros al ejemplo siguiente del constructor.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    El primer parámetro `Style` con nombre `Tabbed`es y su valor es , lo que significa que la ventana será una pestaña en una ventana existente. El parámetro especifica la `Window` posición de acoplamiento, n este caso, el GUID del Explorador de **soluciones**.

    > [!NOTE]
    > Para obtener más información acerca de los <xref:EnvDTE.vsWindowType>tipos de ventanas en el IDE, vea .

## <a name="test-the-tool-window"></a>Pruebe la ventana de herramientas

1. Presione **F5** para abrir una nueva instancia de la compilación experimental de Visual Studio.

2. En el menú **Ver,** seleccione **Otras ventanas** y, a continuación, haga clic en **Primera ventana de herramientas**.

    La ventana de herramientas del reproductor multimedia debe abrirse en la misma posición que el **Explorador**de soluciones. Si sigue apareciendo en la misma posición que antes, restablezca el diseño de la ventana (**Ventana / Restablecer diseño**de ventana ).

3. Haga clic en el botón (tiene el icono **Buscar)** en la ventana de herramientas. Seleccione un archivo de sonido o vídeo compatible, por ejemplo, *C:-windows-media-chimes.wav*y, a continuación, pulse **Abrir**.

    Deberías oír el sonido de la campana.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
