---
title: Suscribirse a un evento | Microsoft Docs
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
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647931"
---
# <a name="subscribing-to-an-event"></a>Suscripción a un evento
En este tutorial se explica cómo crear una ventana de herramientas que responda a los eventos de una tabla de documentos en ejecución (RDT). Una ventana de herramientas hospeda un control de usuario que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> conecta la interfaz con los eventos.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Suscripción a eventos RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Para crear una extensión con una ventana de herramientas

1. Cree un proyecto denominado **RDTExplorer** mediante la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **RDTExplorerWindow**.

     Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Para suscribirse a eventos de RDT

1. Abra el archivo RDTExplorerWindowControl. XAML y elimine el botón denominado `button1`. Agregue un control <xref:System.Windows.Forms.ListBox> y acepte el nombre predeterminado. El elemento Grid debe tener el siguiente aspecto:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Abra el archivo RDTExplorerWindow.cs en la vista de código. Agregue las siguientes directivas using al principio del archivo.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifique la clase `RDTExplorerWindow` para que, además de derivar de la clase <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implemente la interfaz. Coloque el cursor en el nombre de IVsRunningDocTableEvents. Debería ver una bombilla en el margen izquierdo. Haga clic en la flecha hacia abajo situada a la derecha de la bombilla y seleccione **implementar interfaz**.

5. En cada método de la interfaz, reemplace la línea `throw new NotImplementedException();` por esta:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Agregue un campo de cookie a la clase RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Esto contiene la cookie devuelta por el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Invalide el método Initialize () de RDTExplorerWindow para registrar los eventos RDT. Siempre debe obtener los servicios en el método Initialize () de ToolWindowPane, no en el constructor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Se llama al servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> para obtener una interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> conecta eventos RDT a un objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, en este caso, un objeto RDTExplorer.

8. Actualice el método Dispose () de RDTExplorerWindow.

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

     El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> elimina la conexión entre `RDTExplorer` y la notificación de eventos RDT.

9. Agregue la siguiente línea al cuerpo del controlador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>, justo antes de la instrucción `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Agregue una línea similar al cuerpo del controlador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> y a otros eventos que desee ver en el cuadro de lista.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

12. Abra **RDTExplorerWindow** (**Ver/otras ventanas/RDTExplorerWindow**).

     La ventana **RDTExplorerWindow** se abre con una lista de eventos vacía.

13. Abra o cree una solución.

     A medida que se activan los eventos `OnBeforeLastDocument` y `OnAfterFirstDocument`, aparece la notificación de cada evento en la lista de eventos.
