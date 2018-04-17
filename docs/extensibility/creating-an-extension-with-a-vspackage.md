---
title: Crear una extensión con un paquete VSPackage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 706cdcd26df18af9ccd79b5bf83890c47b1faf57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-vspackage"></a>Crear una extensión con un paquete VSPackage
Este tutorial muestra cómo crear un proyecto VSIX y agregar un elemento de proyecto de VSPackage. Usaremos el VSPackage para obtener el servicio de Shell de interfaz de usuario para mostrar un cuadro de mensaje.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Crear un VSPackage  
  
1.  Crear un proyecto VSIX denominado **FirstPackage**. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de paquete de Visual Studio denominada **FirstPackage**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **paquete de Visual Studio**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **FirstPackage.cs**.  
  
3.  Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4.  En la instancia experimental, abra el **herramientas / extensiones y actualizaciones** ventana. Debería ver el **FirstPackage** extensión aquí. (Si abre **extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no verá **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Cargar el VSPackage  
 En este momento la extensión no se carga, porque no hay nada que hace que se va a cargar. Por lo general puede cargar una extensión cuando se interactúa con su interfaz de usuario (al hacer clic en un comando de menú, abra una ventana de herramientas), o mediante la especificación de que el VSPackage debe cargar en un contexto específico de la interfaz de usuario. Para obtener más información sobre la carga de contextos de VSPackages y la interfaz de usuario, consulte [cargar VSPackages](../extensibility/loading-vspackages.md). Para este procedimiento, le mostraremos cómo cargar un paquete VSPackage cuando se abre una solución.  
  
1.  Abra el archivo FirstPackage.cs. Busque la declaración de la clase FirstPackage. Reemplazar los atributos existentes con la siguiente:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Vamos a agregar un mensaje que nos permite saber que ha cargado el VSPackage. Método de Initialize() del VSPackage se usa para realizar esto, porque puede obtener servicios de Visual Studio solo después de que sitúa el VSPackage. (Para obtener más información sobre cómo obtener los servicios, vea [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md).) Reemplace el método Initialize() de FirstPackage con código que obtenga el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de servicio, obtiene la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y las llamadas su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> método.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
4.  Abra una solución en la instancia experimental. Debería ver un cuadro de mensaje que dice **primer paquete dentro de Initialize()**.