---
title: Apertura de una ventana de herramientas dinámicas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702260"
---
# <a name="open-a-dynamic-tool-window"></a>Abrir una ventana de herramientas dinámica
Las ventanas de herramientas normalmente se abren desde un comando de un menú o un método abreviado de teclado equivalente. A veces, sin embargo, es posible que necesite una ventana de herramientas que se abre siempre que se aplica un contexto de interfaz de usuario específico y se cierra cuando el contexto de la interfaz de usuario ya no se aplica. Estos tipos de ventanas de herramientas se denominan *dinámicas* o *autovisibles.*

> [!NOTE]
> Para obtener una lista de contextos de interfaz de usuario predefinidos, vea <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.

 Si desea abrir una ventana de herramientas dinámica según el inicio y es <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> posible que se produzca <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> un error en la creación, debe implementar la interfaz y probar las condiciones de error en el método. Para que el shell sepa que tiene una ventana de herramientas dinámica que `SupportsDynamicToolOwner` se debe abrir al inicio, debe agregar el valor (establecido en 1) al registro del paquete. Este valor no forma <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>parte del estándar, por lo que debe crear un atributo personalizado para agregarlo. Para obtener más información acerca de los atributos personalizados, vea Usar un atributo de [registro personalizado para registrar una extensión.](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)

 Se <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> utiliza para abrir una ventana de herramientas. La ventana de herramientas se crea según sea necesario.

> [!NOTE]
> El usuario puede cerrar una ventana de herramientas dinámica. Si desea crear un comando de menú para que el usuario pueda volver a abrir la ventana de herramientas, el comando de menú debe habilitarse en el mismo contexto de interfaz de usuario que abre la ventana de herramientas y deshabilitarse de lo contrario.

## <a name="to-open-a-dynamic-tool-window"></a>Para abrir una ventana de herramientas dinámica

1. Cree un proyecto VSIX denominado **DynamicToolWindow** y agregue una plantilla de elemento de ventana de herramientas denominada *DynamicWindowPane.cs*. Para obtener más información, consulte Crear una extensión con una ventana de [herramientas.](../extensibility/creating-an-extension-with-a-tool-window.md)

2. En el *DynamicWindowPanePackage.cs* archivo, busque el DynamicWindowPanePackage declaración. Agregue <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> los <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atributos y para registrar la ventana de herramientas.

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

     Los atributos anteriores registran la ventana de herramientas denominada DynamicWindowPane como una ventana transitoria que no se conserva cuando Visual Studio se cierra y se vuelve a abrir. DynamicWindowPane se <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> abre siempre que se aplica y se cierra de lo contrario.

3. Compile la solución y comience la depuración. Debería aparecer la instancia experimental. No debería ver la ventana de herramientas.

4. Abra un proyecto en la instancia experimental. Debería aparecer la ventana de herramientas.
