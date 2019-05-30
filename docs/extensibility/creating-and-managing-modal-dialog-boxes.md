---
title: Creación y administración de cuadros de diálogo modales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2784135b1f3588047e03166a7302f3b8941c564
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338325"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Crear y administrar cuadros de diálogo modales
Cuando se crea un cuadro de diálogo modal en Visual Studio, debe asegurarse de que la ventana primaria del cuadro de diálogo está deshabilitada mientras se muestra el cuadro de diálogo y luego volver a habilitar la ventana primaria cuando se cierra el cuadro de diálogo. Si no lo hace, recibirá el error: *Microsoft Visual Studio no se puede cerrar porque un cuadro de diálogo modal está activo. Cierre el cuadro de diálogo activo e inténtelo de nuevo*

Hay dos maneras de hacerlo. La manera recomendada, si tiene un cuadro de diálogo WPF es derivar desde <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>y, a continuación, llame a <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> para mostrar el cuadro de diálogo. Si lo hace, no es necesario administrar el estado modal de la ventana primaria.

Si el cuadro de diálogo no es WPF o de alguna otra clase no se puede derivar el cuadro de diálogo de motivo <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, a continuación, debe obtener el elemento primario del cuadro de diálogo mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> y administrar el estado modal, mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> método con un parámetro de 0 (false) antes de mostrar el cuadro de diálogo y llamar al método nuevo con un parámetro 1 (verdadero) después de cerrar el cuadro de diálogo.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Crear un cuadro de diálogo derivado de DialogWindow

1. Cree un proyecto VSIX denominado **OpenDialogTest** y agregue un comando de menú llamado **cuadro de diálogo Abrir**. Para obtener más información acerca de cómo hacerlo, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Para usar el <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> (clase), debe agregar referencias a los ensamblados siguientes (en la pestaña .NET Framework de la **Agregar referencia** cuadro de diálogo):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. En *OpenDialog.cs*, agregue las siguientes `using` instrucción:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Declare una clase llamada `TestDialogWindow` que se deriva de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:

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

6. En el `OpenDialog.ShowMessageBox` método, reemplace el código existente con lo siguiente:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Compile y ejecute la aplicación. Debería aparecer la instancia experimental de Visual Studio. En el **herramientas** menú de la instancia experimental debería ver un comando llamado **invocar cuadro de diálogo Abrir**. Al hacer clic en este comando, debería ver el cuadro de diálogo. Debe poder minimizar y maximizar la ventana.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Crear y administrar un cuadro de diálogo no derivado DialogWindow

1. Para este procedimiento, puede usar el **OpenDialogTest** solución creada en el procedimiento anterior, con las mismas referencias de ensamblado.

2. Agregue las siguientes `using` declaraciones:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Cree una clase denominada `TestDialogWindow2` que se deriva de <xref:System.Windows.Window>:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Agregue una referencia privada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```
    private IVsUIShell shell;
    ```

5. Agregue un constructor que establece la referencia a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. En el `OpenDialog.ShowMessageBox` método, reemplace el código existente con lo siguiente:

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

7. Compile y ejecute la aplicación. En el **herramientas** menú debería ver un comando llamado **invocar cuadro de diálogo Abrir**. Al hacer clic en este comando, debería ver el cuadro de diálogo.
