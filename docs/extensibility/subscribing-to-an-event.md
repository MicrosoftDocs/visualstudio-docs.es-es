---
title: "Suscribirse a un evento | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tabla de documento ejecución (RDT), responder a eventos"
  - "tabla de documento ejecución (RDT) para suscribirse a eventos"
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# Suscribirse a un evento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial explica cómo crear una ventana de herramientas que responda a eventos en una tabla de documentos de ejecución \(RDT\). Una ventana de herramientas hospeda un control de usuario que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta con los eventos.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Para suscribirse a eventos RDT  
  
#### Para crear una extensión con una ventana de herramientas  
  
1.  Cree un proyecto denominado **RDTExplorer** utilizando la plantilla VSIX y agregar una plantilla de elemento de ventana de herramientas personalizada denominada **RDTExplorerWindow**.  
  
     Para obtener más información acerca de cómo crear una extensión con una ventana de herramientas, consulte [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### Para suscribirse a eventos RDT  
  
1.  Abra el archivo RDTExplorerWindowControl.xaml y elimine el botón denominado `button1`. Agregar un <xref:System.Windows.Forms.ListBox> controlar y acepte el nombre predeterminado. El elemento de cuadrícula debería tener este aspecto:  
  
    ```xml  
    <Grid> <StackPanel Orientation="Vertical" Margin="-10,10,10,0"> <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock> <ListBox x:Name="listBox" Height="100" /> </StackPanel> </Grid>  
    ```  
  
2.  Abra el archivo RDTExplorerWindow.cs en la vista código. Agregue las siguientes instrucciones using al principio del archivo.  
  
    ```c#  
    using Microsoft.VisualStudio; using Microsoft.VisualStudio.Shell; using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Modificar la `RDTExplorerWindow` lo clase que, además de derivar de la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> \(clase\), que implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfaz.  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents {. . .}  
    ```  
  
4.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Implemente la interfaz. Coloque el cursor en el nombre de IVsRunningDocTableEvents. Debería ver una bombilla en el margen izquierdo. Haga clic en la flecha abajo a la derecha de la bombilla y seleccione **Implementar interfaz**.  
  
5.  En cada método de la interfaz, reemplace la línea `throw new NotImplementedException();` con esto:  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  Agregar un campo de la cookie a la clase RDTExplorerWindow.  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     Esto contiene la cookie devuelta por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> \(método\).  
  
7.  Invalide el método Initialize\(\) del RDTExplorerWindow registrar eventos RDT. Siempre debe obtener servicios en el método Initialize\(\) del ToolWindowPane, no en el constructor.  
  
    ```c#  
    protected override void Initialize() { IVsRunningDocumentTable rdt = (IVsRunningDocumentTable) this.GetService(typeof(SVsRunningDocumentTable)); rdt.AdviseRunningDocTableEvents(this, out rdtCookie); }  
    ```  
  
     El <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> servicio se llama para obtener un <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaz. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta eventos RDT a un objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, en este caso, un objeto RDTExplorer.  
  
8.  El método Dispose\(\) de RDTExplorerWindow Update.  
  
    ```c#  
    protected override void Dispose(bool disposing) { // Release the RDT cookie. IVsRunningDocumentTable rdt = (IVsRunningDocumentTable) Package.GetGlobalService(typeof(SVsRunningDocumentTable)); rdt.UnadviseRunningDocTableEvents(rdtCookie); base.Dispose(disposing); }  
    ```  
  
     El <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> método elimina la conexión entre `RDTExplorer` y notificación de eventos RDT.  
  
9. Agregue la siguiente línea al cuerpo de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> controlador, justo antes del `return` instrucción.  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining) { ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock"); return VSConstants.S_OK; }  
    ```  
  
10. Agregue una línea similar en el cuerpo de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> controlador y a otros eventos que desea ver en el cuadro de lista.  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining) { ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock"); return VSConstants.S_OK; }  
    ```  
  
11. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
12. Abra la **RDTExplorerWindow** \(**vista y otras ventanas \/ RDTExplorerWindow**\).  
  
     El **RDTExplorerWindow** se abre una ventana con una lista de eventos vacío.  
  
13. Abra o cree una solución.  
  
     Como `OnBeforeLastDocument` y `OnAfterFirstDocument` se desencadenan los eventos, notificación de cada evento aparece en el evento de lista.