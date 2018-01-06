---
title: "Abra una ventana de herramientas dinámicas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c96250c79ea283117254a96875c3a1f03f4cb30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="opening-a-dynamic-tool-window"></a>Abra una ventana de herramientas dinámicas
Las ventanas de herramientas normalmente se abren desde un comando en un menú o un método abreviado de teclado equivalente. En ocasiones, sin embargo, puede que tenga una ventana de herramientas que se abre cada vez que se aplica un contexto específico de la interfaz de usuario y se cierra cuando el contexto de la interfaz de usuario ya no es aplicable. Ventanas de herramienta como estas se conocen como *dinámica* o *visibles automáticamente*.  
  
> [!NOTE]
>  Para obtener una lista de contextos de interfaz de usuario predefinidos, vea <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Para el  
  
 Si desea abrir una ventana de herramientas dinámicas en el inicio y es posible que la creación de un error, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> de interfaz y probar las condiciones de error en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> método. Para el shell que sepa que tiene una ventana de herramientas dinámicas que se debe abrir en el inicio, debe agregar el `SupportsDynamicToolOwner` valor (que se establece en 1) en el registro del paquete. Este valor no es parte del estándar <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, por lo que debe crear un atributo personalizado para agregarlo. Para obtener más información sobre atributos personalizados, consulte [mediante un atributo de registro personalizado para registrar una extensión](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir una ventana de herramientas. La ventana de herramientas se crea según sea necesario.  
  
> [!NOTE]
>  El usuario puede cerrar una ventana de herramientas dinámicas. Si desea crear un comando de menú, por lo que el usuario puede volver a abrir la ventana de herramientas, el comando de menú debe estar habilitado en el mismo contexto de interfaz de usuario que se abre la ventana de herramientas y deshabilitado en caso contrario.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Para abrir una ventana de herramientas dinámicas  
  
1.  Crear un proyecto VSIX denominado **DynamicToolWindow** y agregue una plantilla de elemento de ventana de herramienta denominada **DynamicWindowPane.cs**. Para obtener más información, consulte [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  En el archivo DynamicWindowPanePackage.cs, busque la declaración de DynamicWindowPanePackage. Agregar el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y los atributos de T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute para registrar la ventana de herramientas.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Esto registra la ventana de herramienta denominada DynamicWindowPane como una ventana temporal que no se conserva cuando se cierra y se vuelve a abrir Visual Studio. Se abre DynamicWindowPane cada vez que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> se aplica y cerrado en caso contrario.  
  
3.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental. No debería ver la ventana de herramientas.  
  
4.  Abra un proyecto en la instancia experimental. Debe aparecer la ventana de herramientas.