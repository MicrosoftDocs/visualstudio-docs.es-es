---
title: "Creaci&#243;n y administraci&#243;n de cuadros de di&#225;logo modales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cuadros de diálogo, administrar en Visual Studio"
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Creaci&#243;n y administraci&#243;n de cuadros de di&#225;logo modales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se crea un cuadro de diálogo modal dentro de Visual Studio, debe asegurarse de que la ventana primaria del cuadro de diálogo está deshabilitada mientras se muestra el cuadro de diálogo y volver a habilitar la ventana primaria cuando se cierra el cuadro de diálogo. Si no lo hace, podría recibir el error: "Microsoft Visual Studio no se cerró un cuadro de diálogo modal está activo. Cierre el cuadro de diálogo activo e inténtelo de nuevo."  
  
 Hay dos maneras de hacerlo. La manera recomendada, si tiene un cuadro de diálogo WPF es derivar desde <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, y, a continuación, llame a <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> para mostrar el cuadro de diálogo. Si lo hace, no es necesario administrar el estado modal de la ventana primaria.  
  
 Si el cuadro de diálogo no es WPF o de algún otro motivo, no puede derivar su cuadro de diálogo clase de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, debe obtener el elemento primario del cuadro de diálogo mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> y administrar el estado modal, mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> método con un parámetro de 0 \(false\) antes de mostrar el cuadro de diálogo y llamar al método con un parámetro de 1 \(true\) después de cerrar el cuadro de diálogo.  
  
## Crear un cuadro de diálogo derivado de DialogWindow  
  
1.  Cree un proyecto VSIX denominado **OpenDialogTest** y agregue un comando de menú llamado **cuadro de diálogo Abrir**. Para obtener más información acerca de cómo hacerlo, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Usar el <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> \(clase\), debe agregar referencias a los ensamblados siguientes \(en la pestaña de .NET Framework de la **Agregar referencia** cuadro de diálogo\):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  En OpenDialog.cs, agregue la siguiente `using` instrucción:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Declare una clase llamada **TestDialogWindow** que se deriva de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Para poder minimizar y maximizar el cuadro de diálogo, establezca <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> y <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> en true:  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  En el **OpenDialog.ShowMessageBox** método, reemplace el código existente por el siguiente:  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Compile y ejecute la aplicación. Debe aparecer la instancia experimental de Visual Studio. En el **herramientas** menú de la instancia experimental verá un comando llamado **invocar cuadro de diálogo Abrir**. Al hacer clic en este comando, verá el cuadro de diálogo. Debe ser capaz de minimizar y maximizar la ventana.  
  
## Creación y administración de un cuadro de diálogo no derivado de DialogWindow  
  
1.  Para este procedimiento, puede utilizar el **OpenDialogTest** solución creada en el procedimiento anterior, con las mismas referencias de ensamblado.  
  
2.  Agregue las siguientes `using` declaraciones:  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Cree una clase denominada **TestDialogWindow2** que se deriva de <xref:System.Windows.Window>:  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Agregue una referencia privada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Agregue un constructor que establece la referencia a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  En el **OpenDialog.ShowMessageBox** método, reemplace el código existente por el siguiente:  
  
    ```c#  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  Compile y ejecute la aplicación. En el **herramientas** menú verá un comando llamado **invocar cuadro de diálogo Abrir**. Al hacer clic en este comando, verá el cuadro de diálogo.