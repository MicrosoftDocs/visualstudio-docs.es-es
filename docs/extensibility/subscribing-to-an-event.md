---
title: Suscribirse a un evento | Microsoft Docs
description: Obtenga información sobre cómo crear una ventana de herramientas que responda a eventos en una tabla de documentos en ejecución en Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01271016eed9a4a157b333a2f0435589b0a028d5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899398"
---
# <a name="subscribing-to-an-event"></a>Suscripción a un evento
En este tutorial se explica cómo crear una ventana de herramientas que responda a eventos en una tabla de documentos (RDT) en ejecución. Una ventana de herramientas hospeda un control de usuario que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta la interfaz a los eventos.

## <a name="prerequisites"></a>Requisitos previos
 A partir Visual Studio 2015, no se instala el SDK Visual Studio desde el centro de descarga. Se incluye como una característica opcional en Visual Studio configuración. También puede instalar el SDK de VS después. Para obtener más información, consulte [Instalación del SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Suscripción a eventos RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Para crear una extensión con una ventana de herramientas

1. Cree un proyecto denominado **RDTExplorer** con la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **RDTExplorerWindow**.

     Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, vea [Creating an Extension with a Tool Window](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Para suscribirse a eventos RDT

1. Abra el archivo RDTExplorerWindowControl.xaml y elimine el botón denominado `button1` . Agregue un <xref:System.Windows.Forms.ListBox> control y acepte el nombre predeterminado. El elemento Grid debe tener este aspecto:

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

3. Modifique la clase para que, además de derivar de la `RDTExplorerWindow` <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> clase , implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> .

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implemente la interfaz . Coloque el cursor en el nombre de IVsRunningDocTableEvents. Debería ver una bombilla en el margen izquierdo. Haga clic en la flecha Abajo situada a la derecha de la bombilla y seleccione **Implementar interfaz**.

5. En cada método de la interfaz, reemplace la línea `throw new NotImplementedException();` por lo siguiente:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Agregue un campo de cookie a la clase RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Contiene la cookie devuelta por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método .

7. Invalide el método Initialize() de RDTExplorerWindow para registrarse para eventos RDT. Siempre debe obtener servicios en el método Initialize() de ToolWindowPane, no en el constructor .

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Se <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> llama al servicio para obtener una <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaz. El método conecta eventos RDT a un objeto que implementa, en este <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> caso, un objeto RDTExplorer.

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

     El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> método elimina la conexión entre y la notificación de eventos `RDTExplorer` RDT.

9. Agregue la siguiente línea al cuerpo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> controlador, justo antes de la `return` instrucción .

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Agregue una línea similar al cuerpo del controlador y a otros eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> que desee ver en el cuadro de lista.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compile la solución y comience la depuración. Aparece Visual Studio instancia experimental.

12. Abra **RDTExplorerWindow** (**Ver / Otras ventanas / RDTExplorerWindow**).

     La **ventana RDTExplorerWindow** se abre con una lista de eventos vacía.

13. Abra o cree una solución.

     A `OnBeforeLastDocument` medida que se `OnAfterFirstDocument` desencadenan los eventos y , la notificación de cada evento aparece en la lista de eventos.
