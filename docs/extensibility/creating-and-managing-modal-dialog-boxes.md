---
title: Creación y gestión de cuadros de diálogo modales Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739496"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Crear y administrar cuadros de diálogo modales
Al crear un cuadro de diálogo modal dentro de Visual Studio, debe asegurarse de que la ventana primaria del cuadro de diálogo está deshabilitada mientras se muestra el cuadro de diálogo y, a continuación, volver a habilitar la ventana primaria después de cerrar el cuadro de diálogo. Si no lo hace, puede recibir el error: Microsoft Visual Studio no se puede cerrar porque un cuadro de *diálogo modal está activo. Cierre el cuadro de diálogo activo e inténtelo* de nuevo.

Hay dos maneras de hacer esto. La forma recomendada, si tiene un cuadro de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>diálogo WPF, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> es derivarlo de y, a continuación, llamar para mostrar el cuadro de diálogo. Si lo hace, no es necesario administrar el estado modal de la ventana primaria.

Si el cuadro de diálogo no es WPFWPF, o por <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>alguna otra razón no puede derivar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> la clase de cuadro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> diálogo de , a continuación, debe obtener el elemento primario del cuadro de diálogo llamando y administrar el estado modal usted mismo, llamando al método con un parámetro de 0 (false) antes de mostrar el cuadro de diálogo y llamar al método de nuevo con un parámetro de 1 (true) después de cerrar el cuadro de diálogo.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Crear un cuadro de diálogo derivado de DialogWindow

1. Cree un proyecto VSIX denominado **OpenDialogTest** y agregue un comando de menú denominado **OpenDialog**. Para obtener más información sobre cómo hacerlo, vea [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

2. Para usar <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> la clase, debe agregar referencias a los ensamblados siguientes (en la pestaña Marco del cuadro de diálogo **Agregar referencia):**

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. En *OpenDialog.cs*, `using` agregue la siguiente instrucción:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Declare una `TestDialogWindow` clase denominada <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>que derive de:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Para minimizar y maximizar el cuadro <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> diálogo, establezca y en true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. En `OpenDialog.ShowMessageBox` el método, reemplace el código existente por el siguiente:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Compile y ejecute la aplicación. Debería aparecer la instancia experimental de Visual Studio. En el menú **Herramientas** de la instancia experimental debería ver un comando denominado **Invocar OpenDialog**. Al hacer clic en este comando, debería ver la ventana de diálogo. Usted debe ser capaz de minimizar y maximizar la ventana.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Crear y administrar un cuadro de diálogo no derivado de DialogWindow

1. Para este procedimiento, puede usar la solución **OpenDialogTest** que creó en el procedimiento anterior, con las mismas referencias de ensamblado.

2. Agregue las `using` siguientes declaraciones:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Cree una `TestDialogWindow2` clase denominada <xref:System.Windows.Window>que se derive de:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Agregue una referencia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>privada a:

    ```
    private IVsUIShell shell;
    ```

5. Agregue un constructor que <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>establezca la referencia en:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. En `OpenDialog.ShowMessageBox` el método, reemplace el código existente por el siguiente:

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

7. Compile y ejecute la aplicación. En el menú **Herramientas** debería ver un comando denominado **Invocar OpenDialog**. Al hacer clic en este comando, debería ver la ventana de diálogo.
