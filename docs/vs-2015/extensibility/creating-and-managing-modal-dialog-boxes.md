---
title: Crear y administrar cuadros de diálogo modales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b0066f201fbb791d471d5cfb433d9a335aa775
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431581"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Creación y administración de cuadros de diálogo modales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al crear un cuadro de diálogo modal dentro de Visual Studio, debe asegurarse de que la ventana primaria del cuadro de diálogo está deshabilitada mientras se muestra el cuadro de diálogo y, a continuación, volver a habilitar la ventana primaria después de cerrar el cuadro de diálogo. Si no lo hace, es posible que reciba el siguiente error: "Microsoft Visual Studio no se puede cerrar porque un cuadro de diálogo modal está activo. Cierre el cuadro de diálogo activo e inténtelo de nuevo ".  
  
 Hay dos formas de hacerlo. La manera recomendada, si tiene un cuadro de diálogo de WPF, es derivarlo de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> y, a continuación, llama <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> a para mostrar el cuadro de diálogo. Si lo hace, no necesita administrar el estado modal de la ventana primaria.  
  
 Si el cuadro de diálogo no es WPF, o por algún otro motivo por el que no puede derivar la clase de cuadro de diálogo, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> debe obtener el elemento primario del cuadro de diálogo mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> y administrar el estado modal mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> método con un parámetro de 0 (false) antes de mostrar el cuadro de diálogo y volver a llamar al método con un parámetro de 1 (true)  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Crear un cuadro de diálogo derivado de DialogWindow  
  
1. Cree un proyecto VSIX denominado **OpenDialogTest** y agregue un comando de menú denominado **openDialog**. Para obtener más información sobre cómo hacerlo, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Para utilizar la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> clase, debe agregar referencias a los siguientes ensamblados (en la pestaña marco del cuadro de diálogo **Agregar referencia** ):  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - WindowsBase  
  
    - System.Xaml  
  
3. En OpenDialog.cs, agregue la siguiente `using` instrucción:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4. Declare una clase llamada **TestDialogWindow** que se derive de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5. Para poder minimizar y maximizar el cuadro de diálogo, establezca <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> y <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> en true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6. En el método **openDialog. método ShowMessageBox** , reemplace el código existente por lo siguiente:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7. Compile y ejecute la aplicación. Debería aparecer la instancia experimental de Visual Studio. En el menú **herramientas** de la instancia experimental, debería ver un comando denominado **Invoke openDialog**. Al hacer clic en este comando, debería ver la ventana del cuadro de diálogo. Debe poder minimizar y maximizar la ventana.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Crear y administrar un cuadro de diálogo no derivado de DialogWindow  
  
1. Para este procedimiento, puede utilizar la solución **OpenDialogTest** que creó en el procedimiento anterior, con las mismas referencias de ensamblado.  
  
2. Agregue las `using` declaraciones siguientes:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3. Cree una clase denominada **TestDialogWindow2** que se derive de <xref:System.Windows.Window> :  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4. Agregue una referencia privada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5. Agregue un constructor que establezca la referencia a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6. En el método **openDialog. método ShowMessageBox** , reemplace el código existente por lo siguiente:  
  
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
  
7. Compile y ejecute la aplicación. En el menú **herramientas** debería ver un comando llamado **Invoke openDialog**. Al hacer clic en este comando, debería ver la ventana del cuadro de diálogo.
