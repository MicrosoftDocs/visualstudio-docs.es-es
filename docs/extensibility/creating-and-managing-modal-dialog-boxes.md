---
title: Crear y administrar cuadros de diálogo modales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14b1e39e4479b0b6b909c625e1e8b6ad19955d30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Crear y administrar cuadros de diálogo modales
Cuando se crea un cuadro de diálogo modal dentro de Visual Studio, deberá asegurarse de que la ventana primaria del cuadro de diálogo está deshabilitada mientras se muestra el cuadro de diálogo y después volver a habilitar la ventana primaria cuando se cierra el cuadro de diálogo. Si no lo hace, puede recibir el error: "Microsoft Visual Studio no se puede apagar porque un cuadro de diálogo modal está activo. Cierre el cuadro de diálogo activo e inténtelo de nuevo."  
  
 Hay dos maneras de hacerlo. La manera recomendada, si tiene un cuadro de diálogo WPF es derivar desde <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>y, a continuación, llame a <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> para mostrar el cuadro de diálogo. Si lo hace, no es necesario administrar el estado modal de la ventana primaria.  
  
 Si el cuadro de diálogo no es WPF o de alguna otra clase motivo no se puede derivar el cuadro de diálogo de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, a continuación, debe obtener el elemento primario del cuadro de diálogo mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> y administrar el estado modal usted mismo, mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> método con un parámetro de 0 (false) antes de mostrar el cuadro de diálogo y llamar al método nuevo con un parámetro de 1 (verdadero) después de cerrar el cuadro de diálogo.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Crear un cuadro de diálogo derivado de DialogWindow  
  
1.  Crear un proyecto VSIX denominado **OpenDialogTest** y agregue un comando de menú llamado **cuadro de diálogo Abrir**. Para obtener más información acerca de cómo hacerlo, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Para usar el <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> (clase), debe agregar referencias a los ensamblados siguientes (en la pestaña de .NET Framework de la **Agregar referencia** cuadro de diálogo):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  En OpenDialog.cs, agregue las siguientes `using` instrucción:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Declarar una clase denominada **TestDialogWindow** que se deriva de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Para poder minimizar y maximizar el cuadro de diálogo, establezca <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> y <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> en true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  En el **OpenDialog.ShowMessageBox** método, reemplace el código existente con lo siguiente:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Compile y ejecute la aplicación. Debe aparecer la instancia experimental de Visual Studio. En el **herramientas** menú de la instancia experimental verá un comando llamado **cuadro de diálogo Abrir invocar**. Al hacer clic en este comando, verá el cuadro de diálogo. Debe ser capaz de minimizar y maximizar la ventana.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Creación y administración de un cuadro de diálogo no derivado de DialogWindow  
  
1.  Para este procedimiento, puede usar el **OpenDialogTest** solución creada en el procedimiento anterior, con las mismas referencias de ensamblado.  
  
2.  Agregue las siguientes `using` declaraciones:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Cree una clase denominada **TestDialogWindow2** que se deriva de <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Agregue una referencia privada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Agregue un constructor que establece la referencia a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  En el **OpenDialog.ShowMessageBox** método, reemplace el código existente con lo siguiente:  
  
    ```csharp  
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
  
7.  Compile y ejecute la aplicación. En el **herramientas** menú verá un comando llamado **cuadro de diálogo Abrir invocar**. Al hacer clic en este comando, verá el cuadro de diálogo.