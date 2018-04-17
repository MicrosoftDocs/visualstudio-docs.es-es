---
title: Abra una ventana de herramientas dinámicas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd3a4a8d85ed7d0f5884e7f11b8778eb3b420a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="opening-a-dynamic-tool-window"></a>Abra una ventana de herramientas dinámicas
Las ventanas de herramientas normalmente se abren desde un comando en un menú o un método abreviado de teclado equivalente. En ocasiones, sin embargo, puede que tenga una ventana de herramientas que se abre cada vez que se aplica un contexto específico de la interfaz de usuario y se cierra cuando el contexto de la interfaz de usuario ya no es aplicable. Estos tipos de ventanas de herramientas se denominan *dinámica* o *visibles automáticamente*.  
  
> [!NOTE]
>  Para obtener una lista de contextos de interfaz de usuario predefinidos, vea <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Para el  
  
 Si desea abrir una ventana de herramientas dinámicas en el inicio y es posible que la creación de un error, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> de interfaz y probar las condiciones de error en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> método. Para el shell que sepa que tiene una ventana de herramientas dinámicas que se debe abrir en el inicio, debe agregar el `SupportsDynamicToolOwner` valor (que se establece en 1) en el registro del paquete. Este valor no es parte del estándar <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, por lo que debe crear un atributo personalizado para agregarlo. Para obtener más información sobre atributos personalizados, consulte [mediante un atributo de registro personalizado para registrar una extensión](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir una ventana de herramientas. La ventana de herramientas se crea según sea necesario.  
  
> [!NOTE]
>  El usuario puede cerrar una ventana de herramientas dinámicas. Si desea crear un comando de menú, por lo que el usuario puede volver a abrir la ventana de herramientas, el comando de menú debe estar habilitado en el mismo contexto de interfaz de usuario que se abre la ventana de herramientas y deshabilitado en caso contrario.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Para abrir una ventana de herramientas dinámicas  
  
1.  Crear un proyecto VSIX denominado **DynamicToolWindow** y agregue una plantilla de elemento de ventana de herramienta denominada **DynamicWindowPane.cs**. Para obtener más información, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  En el archivo DynamicWindowPanePackage.cs, busque la declaración de DynamicWindowPanePackage. Agregar el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atributos para registrar la ventana de herramientas.  
  
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
  
     Los atributos anteriores registrar la ventana de herramienta denominada DynamicWindowPane como una ventana temporal que no se conserva cuando se cierra y se vuelve a abrir Visual Studio. Se abre DynamicWindowPane cada vez que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> se aplica y cerrado en caso contrario.  
  
3.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental. No debería ver la ventana de herramientas.  
  
4.  Abra un proyecto en la instancia experimental. Debe aparecer la ventana de herramientas.