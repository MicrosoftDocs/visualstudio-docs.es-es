---
title: Suscribirse a un evento ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699683"
---
# <a name="subscribing-to-an-event"></a>Suscripción a un evento
En este tutorial se explica cómo crear una ventana de herramientas que responde a eventos en una tabla de documentos en ejecución (RDT). Una ventana de herramientas hospeda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>un control de usuario que implementa . El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta la interfaz con los eventos.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="subscribing-to-rdt-events"></a>Suscribirse a eventos RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Para crear una extensión con una ventana de herramientas

1. Cree un proyecto denominado **RDTExplorer** mediante la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **RDTExplorerWindow**.

     Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, consulte [Creación de una extensión con una ventana](../extensibility/creating-an-extension-with-a-tool-window.md)de herramientas .

#### <a name="to-subscribe-to-rdt-events"></a>Para suscribirse a eventos rdto

1. Abra el archivo RDTExplorerWindowControl.xaml y `button1`elimine el botón denominado . Agregue <xref:System.Windows.Forms.ListBox> un control y acepte el nombre predeterminado. El elemento Grid debe tener este aspecto:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Abra el archivo RDTExplorerWindow.cs en la vista de código. Agregue las siguientes directivas using al inicio del archivo.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifique `RDTExplorerWindow` la clase para que, además de derivar de la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> clase, implemente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfaz.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implemente la interfaz. Coloque el cursor en el nombre IVsRunningDocTableEvents. Debería ver una bombilla en el margen izquierdo. Haga clic en la flecha abajo a la derecha de la bombilla y seleccione **Implementar interfaz**.

5. En cada método en la `throw new NotImplementedException();` interfaz, substituya la línea con esto:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Agregue un campo de cookie a la clase RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Esto contiene la cookie que <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> devuelve el método.

7. Invalide el método Initialize() de RDTExplorerWindow para registrarse para eventos RDT. Siempre debe obtener servicios en el ToolWindowPane Initialize() método, no en el constructor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Se <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> llama al servicio <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> para obtener una interfaz. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta eventos RDT a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>un objeto que implementa , en este caso, un objeto RDTExplorer.

8. Actualice el método Dispose() de RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> método elimina la `RDTExplorer` conexión entre y la notificación de eventos RDT.

9. Agregue la siguiente línea al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> cuerpo del `return` controlador, justo antes de la instrucción.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Agregue una línea similar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> cuerpo del controlador y a otros eventos que desee ver en el cuadro de lista.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

12. Abra **la ventana RDTExplorerWindow** (**Ver / Otras ventanas / RDTExplorerWindow**).

     La ventana **RDTExplorerWindow** se abre con una lista de eventos vacía.

13. Abra o cree una solución.

     A `OnBeforeLastDocument` `OnAfterFirstDocument` medida que se desencadenan los eventos, la notificación de cada evento aparece en la lista de eventos.
