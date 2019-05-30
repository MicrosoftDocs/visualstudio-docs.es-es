---
title: Suscripción a un evento | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c0466d5b8644ddeae60df24b8b980ee9da0f820
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331683"
---
# <a name="subscribing-to-an-event"></a>Suscripción a un evento
En este tutorial se explica cómo crear una ventana de herramientas que responde a los eventos en una tabla de documentos en ejecución (RDT). Una ventana de herramientas hospeda un control de usuario que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta con los eventos.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Suscribirse a eventos RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Para crear una extensión con una ventana de herramientas

1. Cree un proyecto denominado **RDTExplorer** con la plantilla VSIX y agrega una plantilla de elemento de ventana de herramienta personalizada denominada **RDTExplorerWindow**.

     Para obtener más información acerca de cómo crear una extensión con una ventana de herramientas, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Para suscribirse a eventos RDT

1. Abra el archivo RDTExplorerWindowControl.xaml y elimine el botón denominado `button1`. Agregar un <xref:System.Windows.Forms.ListBox> controlar y acepte el nombre predeterminado. El elemento de cuadrícula debería tener este aspecto:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Abra el archivo RDTExplorerWindow.cs en la vista código. Agregue las siguientes instrucciones using al principio del archivo.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modificar el `RDTExplorerWindow` lo clase que, además de derivar de la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> (clase), implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfaz.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implemente la interfaz. Coloque el cursor en el nombre IVsRunningDocTableEvents. Debería ver una bombilla en el margen izquierdo. Haga clic en la flecha abajo a la derecha de la bombilla y seleccione **Implementar interfaz**.

5. Cada método en la interfaz, reemplace la línea `throw new NotImplementedException();` con esto:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Agregue un campo de la cookie a la clase RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Esto contiene la cookie devuelta por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método.

7. Invalide el método Initialize() del RDTExplorerWindow registrarse para eventos RDT. Siempre debe obtener servicios en el método Initialize() del ToolWindowPane, no en el constructor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     El <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> servicio se llama para obtener un <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaz. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta los eventos RDT para un objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, en este caso, un objeto RDTExplorer.

8. El método Dispose() de RDTExplorerWindow Update.

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

     El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> método elimina la conexión entre `RDTExplorer` y notificación de eventos RDT.

9. Agregue la línea siguiente al cuerpo de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> controlador, justo antes del `return` instrucción.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Agregue una línea similar en el cuerpo de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> controlador y a otros eventos que desea ver en el cuadro de lista.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

12. Abra el **RDTExplorerWindow** (**vista / otros Windows / RDTExplorerWindow**).

     El **RDTExplorerWindow** se abre una ventana con una lista de eventos vacío.

13. Abra o cree una solución.

     Como `OnBeforeLastDocument` y `OnAfterFirstDocument` se activan los eventos, notificación de cada evento aparece en el evento de lista.