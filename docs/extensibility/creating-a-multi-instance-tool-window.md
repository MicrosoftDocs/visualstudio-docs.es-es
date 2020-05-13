---
title: Creación de una ventana de herramientas de varias instancias (Multi-Instance Tool Window) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739628"
---
# <a name="create-a-multi-instance-tool-window"></a>Crear una ventana de herramientas de varias instancias
Puede programar una ventana de herramientas para que varias instancias de la misma se puedan abrir simultáneamente. De forma predeterminada, las ventanas de herramientas solo pueden tener una instancia abierta.

Cuando se utiliza una ventana de herramientas de varias instancias, puede mostrar varias fuentes de información relacionadas al mismo tiempo. Por ejemplo, podría colocar un <xref:System.Windows.Forms.TextBox> control de varias líneas en una ventana de herramientas de varias instancias para que varios fragmentos de código estén disponibles simultáneamente durante una sesión de programación. Además, por ejemplo, <xref:System.Windows.Forms.DataGrid> podría colocar un control y un cuadro de lista desplegable en una ventana de herramientas de varias instancias para que se pueda realizar un seguimiento simultánea de varios orígenes de datos en tiempo real.

## <a name="create-a-basic-single-instance-tool-window"></a>Crear una ventana de herramientas básica (de instancia única)

1. Cree un proyecto denominado **MultiInstanceToolWindow** con la plantilla VSIX y agregue una plantilla de elemento de ventana de herramientas personalizada denominada **MIToolWindow**.

    > [!NOTE]
    > Para obtener más información sobre cómo crear una extensión con una ventana de herramientas, consulte [Crear una extensión con una ventana](../extensibility/creating-an-extension-with-a-tool-window.md)de herramientas .

## <a name="make-a-tool-window-multi-instance"></a>Hacer una ventana de herramientas multiinstancia

1. Abra *MIToolWindowPackage.cs* el archivo MIToolWindowPackage.cs `ProvideToolWindow` y busque el atributo. y `MultiInstances=true` el parámetro, como se muestra en el ejemplo siguiente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. En el *archivo MIToolWindowCommand.cs,* busque el `ShowToolWindos()` método. En este método, <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> llame al `create` método `false` y establezca su marca para que iterará `id` a través de las instancias de ventana de herramientas existentes hasta que se encuentre una disponible.

3. Para crear una instancia de <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> ventana de `id` herramientas, llame `create` al `true`método y establezca su valor en un valor disponible y su marca en .

    De forma predeterminada, `id` el valor <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> del `0`parámetro del método es . Este valor crea una ventana de herramientas de instancia única. Para que se hospede más de una `id`instancia, cada instancia debe tener su propio archivo .

4. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> en el objeto <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> devuelto por la propiedad de la instancia de la ventana de herramientas.

5. De forma `ShowToolWindow` predeterminada, el método creado por la plantilla de elemento de la ventana de herramientas crea una ventana de herramientas de instancia única. En el ejemplo siguiente `ShowToolWindow` se muestra cómo modificar el método para crear varias instancias.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
