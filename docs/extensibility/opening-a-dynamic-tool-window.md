---
title: Abrir una ventana de herramientas dinámica | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6e44a0f1be3c9ac48ad41c5b74562059f60d3f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945156"
---
# <a name="open-a-dynamic-tool-window"></a>Abra una ventana de herramientas dinámica
Ventanas de herramientas normalmente se abren desde un comando en un menú o un método abreviado de teclado equivalente. En ocasiones, sin embargo, puede necesitar una ventana de herramientas que se abre cada vez que se aplica un contexto específico de la interfaz de usuario y se cierra cuando ya no se aplica el contexto de interfaz de usuario. Estos tipos de ventanas de herramientas se denominan *dinámica* o *visibles automáticamente*.  
  
> [!NOTE]
>  Para obtener una lista de contextos de interfaz de usuario predefinidos, vea <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.  
  
 Si desea abrir una ventana de herramientas dinámica al inicio y es posible que la creación de un error, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfaz y probar las condiciones de error en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> método. En el orden en que se sabe que tiene una ventana de herramientas dinámica que se debe abrir en el inicio el shell, debe agregar el `SupportsDynamicToolOwner` valor (que se establece en 1) en el registro del paquete. Este valor no es parte del estándar <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, por lo que debe crear un atributo personalizado para agregarlo. Para obtener más información sobre atributos personalizados, consulte [utilizar un atributo de registro personalizado para registrar una extensión](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir una ventana de herramientas. La ventana de herramientas se crea según sea necesario.  
  
> [!NOTE]
>  El usuario puede cerrar una ventana de herramientas dinámica. Si desea crear un comando de menú para que el usuario puede volver a abrir la ventana de herramientas, el comando de menú debe habilitarse en el mismo contexto de interfaz de usuario que se abre la ventana de herramientas y deshabilitado en caso contrario.  
  
## <a name="to-open-a-dynamic-tool-window"></a>Para abrir una ventana de herramientas dinámica  
  
1.  Cree un proyecto VSIX denominado **DynamicToolWindow** y agregar una plantilla de elemento de ventana de herramienta denominada *DynamicWindowPane.cs*. Para obtener más información, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  En el *DynamicWindowPanePackage.cs* de archivos, busque la declaración de DynamicWindowPanePackage. Agregar el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atributos para registrar la ventana de herramientas.  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Los atributos anteriores registrar la ventana de herramientas denominada DynamicWindowPane como una ventana transitoria que no se conserva cuando se cierra y vuelve a abrir Visual Studio. Se abre DynamicWindowPane cada vez que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> se aplica y cerrado en caso contrario.  
  
3.  Compile la solución y comience la depuración. Debería aparecer la instancia experimental. No debería ver la ventana de herramientas.  
  
4.  Abra un proyecto en la instancia experimental. Debería aparecer la ventana de herramientas.