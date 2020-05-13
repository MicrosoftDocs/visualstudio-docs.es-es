---
title: Creación de una extensión con un VSPackage ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739528"
---
# <a name="create-an-extension-with-a-vspackage"></a>Crear una extensión con un VSPackage

En este tutorial se muestra cómo crear un proyecto VSIX y agregar un elemento de proyecto de VSPackage. Usaremos el VSPackage para obtener el servicio DeI Shell con el fin de mostrar un cuadro de mensaje.

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-vspackage"></a>Crear un VSPackage

1. Cree un proyecto VSIX denominado **FirstPackage**. Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de paquete de Visual Studio denominada **FirstPackage**. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione Paquete de **Visual Studio**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *FirstPackage.cs*.

3. Compile la solución y comience la depuración.

    Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [La instancia experimental](../extensibility/the-experimental-instance.md).

4. En la instancia experimental, abra la ventana**Extensiones y actualizaciones** de **herramientas.** >  Debería ver la extensión **FirstPackage** aquí. (Si abre **Extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no verá **FirstPackage**).

## <a name="load-the-vspackage"></a>Cargar el VSPackage

En este momento, la extensión no se carga porque no hay nada que haga que se cargue. Por lo general, puede cargar una extensión cuando interactúa con su interfaz de usuario (haciendo clic en un comando de menú, abrir una ventana de herramientas) o especificando que el VSPackage debe cargar se carga en un contexto de interfaz de usuario específico. Para obtener más información acerca de cómo cargar VSPackages y contextos de interfaz de usuario, vea [cargar VSPackages](../extensibility/loading-vspackages.md). Para este procedimiento, le mostraremos cómo cargar un VSPackage cuando una solución está abierta.

1. Abra el archivo *FirstPackage.cs.* Busque la declaración `FirstPackage` de la clase. Sustituya los atributos existentes por los siguientes atributos:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Vamos a agregar un mensaje que nos permite saber que el VSPackage se ha cargado. Usamos el método `Initialize()` de VSPackage para hacer esto, porque puede obtener servicios de Visual Studio solo después de que el VSPackage se ha sitio. (Para obtener más información acerca de cómo obtener servicios, consulte [Cómo: Obtener un servicio](../extensibility/how-to-get-a-service.md).) Reemplace `Initialize()` el `FirstPackage` método de código <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> que obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> servicio, obtiene <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> la interfaz y llama a su método.

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

3. Compile la solución y comience la depuración. Aparece la instancia experimental.

4. Abra una solución en la instancia experimental. Debería ver un cuadro de mensaje que dice **First Package Inside Initialize()**.
