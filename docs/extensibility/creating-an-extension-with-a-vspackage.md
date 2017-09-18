---
title: "Crear una extensi&#243;n con un VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Crear una extensi&#243;n con un VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo crear un proyecto de VSIX y agregar un elemento de proyecto de VSPackage. Usaremos el VSPackage para obtener el servicio de Shell de interfaz de usuario para mostrar un cuadro de mensaje.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creación de un paquete VSPackage  
  
1.  Cree un proyecto VSIX denominado **FirstPackage**. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de paquete de Visual Studio denominada **FirstPackage**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **paquete de Visual Studio**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **FirstPackage.cs**.  
  
3.  Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4.  En la instancia experimental, abra el **Herramientas \/ extensiones y actualizaciones** ventana. Debería ver el **FirstPackage** extensión aquí. \(Si abre **extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no podrá ver **FirstPackage**\).  
  
## Cargar el VSPackage  
 En este momento la extensión no se carga, porque no hay nada que provoca que se va a cargar. Por lo general, puede cargar una extensión al interactuar con su interfaz de usuario \(al hacer clic en un comando de menú, abra una ventana de herramientas\) o especificando que el VSPackage se cargará en un contexto específico de la interfaz de usuario. Para obtener más información acerca de cómo cargar VSPackages y UI contextos, consulte [Cargar VSPackages](../extensibility/loading-vspackages.md). Para este procedimiento, le mostraremos cómo cargar un paquete VSPackage cuando se abre una solución.  
  
1.  Abra el archivo FirstPackage.cs. Busque la declaración de la clase FirstPackage. Reemplace los atributos existentes por el siguiente:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Vamos a agregar un mensaje que nos permite saber que se ha cargado el VSPackage. Usamos método Initialize\(\) de VSPackage para hacer esto, ya que puede obtener los servicios de Visual Studio después de que se sitúa el VSPackage. \(Para obtener más información sobre servicios, consulte [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md).\) Reemplace el método Initialize\(\) del FirstPackage por código que obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servicio obtiene la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y llama su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> método.  
  
    ```c#  
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
  
4.  Abra una solución en la instancia experimental. Debería ver un cuadro de mensaje que dice **primer paquete dentro de Initialize\(\)**.