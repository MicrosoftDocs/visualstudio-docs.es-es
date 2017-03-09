---
title: "Abrir una ventana de herramientas mediante programaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, crear mediante programación"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Abrir una ventana de herramientas mediante programaci&#243;n
Las ventanas de herramientas normalmente se abren haciendo clic en un comando de un menú o presionando un método abreviado de teclado equivalente. Sin embargo, es posible que deba abrir una ventana de herramientas mediante programación, como lo hace el controlador de comandos.  
  
 Para abrir una ventana de herramientas en el paquete VSPackage administrado que la proporciona, use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>. Para abrir una ventana de herramientas en otro VSPackage, use <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>. En cualquier caso, se crea la ventana de herramientas según sea necesario.  
  
 El código siguiente se toma del ejemplo de C\# Reference.ToolWindow.  
  
### Para abrir una ventana de herramientas mediante programación  
  
1.  Cree el panel de la ventana de herramientas, el marco y el VSPackage que los implementa. Para obtener más información, consulte [Agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
2.  Agregue la clase <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> al VSPackage que la proporciona.  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     Esto registra la ventana de herramientas PersistedWindowPane para que se abra como acoplada al **Explorador de soluciones**. Para obtener más información, consulte [Registrar una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
3.  Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para encontrar el panel de la ventana de herramientas o para crearlo si aún no existe.  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  Obtenga el marco de ventana de herramientas desde el panel de la ventana de herramientas.  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  Muestre la ventana de herramientas.  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```