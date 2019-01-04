---
title: Creación de una ventana de herramientas de instancias múltiples | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c8652531379d880d44622a4f896f5a30151cdc5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860366"
---
# <a name="create-a-multi-instance-tool-window"></a>Crear una ventana de herramientas de instancias múltiples
Puede programar una ventana de herramientas para que varias instancias del mismo pueden abrir simultáneamente. De forma predeterminada, las ventanas de herramientas pueden tener solo una instancia de abrir.  
  
 Cuando se utiliza una ventana de herramientas de varias instancias, puede mostrar varios orígenes relacionados de información al mismo tiempo. Por ejemplo, podría poner un multilínea <xref:System.Windows.Forms.TextBox> control en una ventana de herramientas de varias instancias de modo que varios fragmentos de código están disponibles de forma simultánea durante una sesión de programación. Además, por ejemplo, podría colocar un <xref:System.Windows.Forms.DataGrid> cuadro y una lista desplegable de control en una ventana de herramientas de varias instancias para que varios orígenes de datos en tiempo real pueden controlarse de forma simultánea.  
  
## <a name="create-a-basic-single-instance-tool-window"></a>Crear una ventana de herramientas (instancia única) básica  
  
1.  Cree un proyecto denominado **MultiInstanceToolWindow** con la plantilla VSIX y agrega una plantilla de elemento de ventana de herramienta personalizada denominada **MIToolWindow**.  
  
    > [!NOTE]
    >  Para obtener más información acerca de cómo crear una extensión con una ventana de herramientas, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="make-a-tool-window-multi-instance"></a>Crear una instancia de múltiples de ventana de herramienta  
  
1.  Abra el *MIToolWindowPackage.cs* de archivo y busque el `ProvideToolWindow` atributo. y el `MultiInstances=true` parámetro, tal como se muestra en el ejemplo siguiente:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  En el *MIToolWindowCommand.cs* de archivos, busque el `ShowToolWindos()` método. En este método, llame a la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método y establezca su `create` marca a `false` para que creará una iteración a través de las instancias de la ventana de herramienta existentes hasta que esté disponible `id` se encuentra.  
  
3.  Para crear una instancia de la ventana de herramienta, llame a la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método y establezca su `id` en un valor disponible y su `create` marca a `true`.  
  
     De forma predeterminada, el valor de la `id` parámetro de la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método es `0`. Este valor hace que una ventana de herramientas de instancia única. Para que más de una instancia hospedarse, cada instancia debe tener su propia `id`.  
  
4.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto devuelto por la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> propiedad de la instancia de la ventana de herramienta.  
  
5.  De forma predeterminada, el `ShowToolWindow` método que se crea mediante la plantilla de elemento de la ventana de herramienta crea una ventana de herramientas de instancia única. El ejemplo siguiente muestra cómo modificar el `ShowToolWindow` método para crear varias instancias.  
  
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