---
title: "Abrir una ventana de herramientas din&#225;mica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, de forma dinámicas"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Abrir una ventana de herramientas din&#225;mica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ventanas de herramientas normalmente se abren desde un comando en un menú o un método abreviado de teclado equivalente. A veces, sin embargo, puede que tenga una ventana de herramientas que se abre cada vez que se aplica un contexto específico de la interfaz de usuario y se cierra cuando ya no se aplica el contexto de la IU. Ventanas de herramientas como éstas se denominan *dinámica* o *automáticamente visible*.  
  
> [!NOTE]
>  Para obtener una lista de contextos de la interfaz de usuario predefinidos, consulte <xref:Microsoft.VisualStudio.VSConstants.UIContext>. Para la  
  
 Si desea abrir una ventana de herramientas dinámica durante el inicio y es posible que la creación de un error, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> de la interfaz y probar las condiciones de error en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> \(método\). Para el shell sabe que tiene una ventana de herramientas dinámica que debe abrirse al inicio, debe agregar el `SupportsDynamicToolOwner` valor \(establecida en 1\) en el registro del paquete. Este valor no es parte del estándar <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, por lo que debe crear un atributo personalizado para agregarlo. Para obtener más información sobre atributos personalizados, consulte [Usar un atributo de registro personalizado para registrar una extensión](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir una ventana de herramientas. La ventana de herramientas se crea según sea necesario.  
  
> [!NOTE]
>  El usuario puede cerrar una ventana de herramientas dinámica. Si desea crear un comando de menú para que el usuario puede volver a abrir la ventana de herramientas, el comando de menú debe estar habilitado en el mismo contexto de interfaz de usuario que se abre la ventana de herramienta y deshabilitada en caso contrario.  
  
### Para abrir una ventana de herramientas dinámica  
  
1.  Cree un proyecto VSIX denominado **DynamicToolWindow** y agregue una plantilla de elemento de ventana de herramienta denominada **DynamicWindowPane.cs**. Para obtener más información, consulta [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  En el archivo DynamicWindowPanePackage.cs, busque la declaración de DynamicWindowPanePackage. Agregue el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y los atributos de T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute para registrar la ventana de herramientas.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     Esto registra la ventana de herramientas denominada DynamicWindowPane como una ventana temporal que no se conserva cuando se cierra y se vuelve a abrir Visual Studio. Se abre DynamicWindowPane cada vez que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> se aplica y cerrado en caso contrario.  
  
3.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental. No verá la ventana de herramientas.  
  
4.  Abra un proyecto en la instancia experimental. Debe aparecer la ventana de herramientas.