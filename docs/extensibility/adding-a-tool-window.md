---
title: Agregar una ventana de herramientas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 169f386128ccdd79aef6b90a6703f50323b9b6f3
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904135"
---
# <a name="add-a-tool-window"></a>Agregar una ventana de herramientas

En este tutorial aprenderá a crear una ventana de herramientas e integrarla en Visual Studio de las maneras siguientes:

- Agregue un control a la ventana de herramientas.

- Agregar una barra de herramientas a una ventana de herramientas.

- Agregue un comando a la barra de herramientas.

- Implemente los comandos.

- Establezca la posición predeterminada de la ventana de herramientas.

## <a name="prerequisites"></a>Requisitos previos

El SDK de Visual Studio se incluye como una característica opcional en el programa de instalación de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Crear una ventana de herramientas

1. Cree un proyecto denominado **FirstToolWin** mediante la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **FirstToolWindow**.

    > [!NOTE]
    > Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Agregar un control a la ventana de herramientas

1. Quite el control predeterminado. Abra *FirstToolWindowControl. Xaml* y elimine el **click me** . .

2. En el **cuadro de herramientas**, expanda la sección **todos los controles WPF** y arrastre el control **elemento multimedia** hasta el formulario **FirstToolWindowControl** . Seleccione el control y, en la ventana **propiedades** , asigne el nombre **mediaElement1**a este elemento.

## <a name="add-a-toolbar-to-the-tool-window"></a>Agregar una barra de herramientas a la ventana de herramientas
Al agregar una barra de herramientas de la siguiente manera, garantiza que sus degradados y colores son coherentes con el resto del IDE.

1. En **Explorador de soluciones**, Abra *FirstToolWindowPackage. Vsct*. El archivo *. Vsct* define los elementos de la interfaz gráfica de usuario (GUI) en la ventana de herramientas mediante XML.

2. En la `<Symbols>` sección, busque el `<GuidSymbol>` nodo cuyo `name` atributo es `guidFirstToolWindowPackageCmdSet` . Agregue los dos `<IDSymbol>` elementos siguientes a la lista de `<IDSymbol>` elementos de este nodo para definir una barra de herramientas y un grupo de barras de herramientas.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Justo encima de la `<Buttons>` sección, cree una `<Menus>` sección similar a la siguiente:

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

    Hay varios tipos diferentes de menús. Este menú es una barra de herramientas en una ventana de herramientas, definida por su `type` atributo. La `guid` configuración de y `id` constituye el identificador completo de la barra de herramientas. Normalmente, el `<Parent>` de un menú es el grupo contenedor. Sin embargo, una barra de herramientas se define como su propio elemento primario. Por lo tanto, se usa el mismo identificador para `<Menu>` los `<Parent>` elementos y. El `priority` atributo es simplemente ' 0 '.

4. Las barras de herramientas se parecen a los menús de muchas maneras. Por ejemplo, al igual que un menú puede tener grupos de comandos, las barras de herramientas también pueden tener grupos. (En los menús, los grupos de comandos están separados por líneas horizontales. En las barras de herramientas, los grupos no están separados por divisores visuales).

    Agregue una `<Groups>` sección que contenga un `<Group>` elemento. Esto define el grupo cuyo identificador se declaró en la `<Symbols>` sección. Agregue la `<Groups>` sección justo después de la `<Menus>` sección.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Al establecer el GUID y el identificador principales en el GUID y el identificador de la barra de herramientas, se agrega el grupo a la barra de herramientas.

## <a name="add-a-command-to-the-toolbar"></a>Agregar un comando a la barra de herramientas

Agregue un comando a la barra de herramientas, que se muestra como un botón.

1. En la `<Symbols>` sección, declare los siguientes elementos IDSymbol justo después de las declaraciones de grupo Toolbar y Toolbar.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Agregue un elemento Button dentro de la `<Buttons>` sección. Este elemento aparecerá en la barra de herramientas de la ventana de herramientas, con un icono de **búsqueda** (lupa).

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

3. Abra *FirstToolWindowCommand.CS* y agregue las líneas siguientes en la clase justo después de los campos existentes.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Esto hace que los comandos estén disponibles en el código.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Agregar una propiedad MediaPlayer a FirstToolWindowControl
Desde los controladores de eventos para los controles de barra de herramientas, el código debe poder tener acceso al control Media Player, que es un elemento secundario de la clase FirstToolWindowControl.

En **Explorador de soluciones**, haga clic con el botón secundario en *FirstToolWindowControl. Xaml*, haga clic en **Ver código**y agregue el código siguiente a la clase FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Crear una instancia de la ventana de herramientas y la barra de herramientas
Agregue una barra de herramientas y un comando de menú que invoque el cuadro de diálogo **Abrir archivo** y reproduzca el archivo multimedia seleccionado.

1. Abra *FirstToolWindow.CS* y agregue las siguientes `using` directivas:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Dentro de la clase FirstToolWindow, agregue una referencia pública al control FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Al final del constructor, establezca esta variable de control en el control que se acaba de crear.

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

5. En este momento, el constructor FirstToolWindow debe tener el siguiente aspecto:

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

7. En la clase FirstToolWindowCommand, agregue el código siguiente al final del método ShowToolWindow (). El comando ButtonHandler se implementará en la sección siguiente.

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

1. En la clase FirstToolWindowCommand, agregue un método ButtonHandler que invoque el cuadro de diálogo **Abrir archivo** . Cuando se ha seleccionado un archivo, reproduce el archivo multimedia.

2. En la clase FirstToolWindowCommand, agregue una referencia privada a la ventana FirstToolWindow que se crea en el método FindToolWindow ().

    ```csharp
    private FirstToolWindow window;
    ```

3. Cambie el método ShowToolWindow () para establecer la ventana que definió anteriormente (para que el controlador de comandos ButtonHandler pueda tener acceso al control de ventana. Este es el método ShowToolWindow () completo.

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

4. Agregue el método ButtonHandler. Crea un OpenFileDialog para que el usuario especifique el archivo multimedia que se va a reproducir y, a continuación, reproduce el archivo seleccionado.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Establecer la posición predeterminada de la ventana de herramientas

A continuación, especifique una ubicación predeterminada en el IDE para la ventana de herramientas. La información de configuración de la ventana de herramientas se encuentra en el archivo *FirstToolWindowPackage.CS* .

1. En *FirstToolWindowPackage.CS*, busque el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atributo en la `FirstToolWindowPackage` clase, que pasa el tipo FirstToolWindow al constructor. Para especificar una posición predeterminada, debe agregar más parámetros al ejemplo siguiente.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    El primer parámetro con nombre es `Style` y su valor es `Tabbed` , lo que significa que la ventana será una pestaña de una ventana existente. La posición de acoplamiento se especifica mediante el `Window` parámetro, n este caso, el GUID del **Explorador de soluciones**.

    > [!NOTE]
    > Para obtener más información acerca de los tipos de ventanas en el IDE, vea <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Probar la ventana de herramientas

1. Presione **F5** para abrir una nueva instancia de la compilación experimental de Visual Studio.

2. En el menú **Ver** , seleccione **otras ventanas** y, a continuación, haga clic en **primera ventana de herramientas**.

    La ventana de herramientas del reproductor de media debe abrirse en la misma posición que **Explorador de soluciones**. Si todavía aparece en la misma posición que antes, restablezca el diseño de ventana (**ventana/restablecer diseño de ventana**).

3. Haga clic en el botón (tiene el icono de **búsqueda** ) en la ventana de herramientas. Seleccione un archivo de sonido o de vídeo compatible, por ejemplo, *C:\windows\media\chimes.wav*y, a continuación, presione **abrir**.

    Debería oír el sonido del avisador.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
