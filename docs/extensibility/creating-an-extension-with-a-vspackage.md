---
title: Crear una extensión con un VSPackage | Microsoft Docs
description: Obtenga información sobre cómo crear un proyecto de VSIX y agregar un elemento de proyecto de VSPackage mediante el VSPackage para obtener el servicio de Shell de interfaz de usuario con el fin de mostrar un cuadro de mensaje.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6c93d90771eeffbfe28ae91781403019743afa9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089152"
---
# <a name="create-an-extension-with-a-vspackage"></a>Creación de una extensión con un VSPackage

En este tutorial se muestra cómo crear un proyecto de VSIX y agregar un elemento de proyecto de VSPackage. Usaremos el VSPackage para obtener el servicio de Shell de interfaz de usuario con el fin de mostrar un cuadro de mensaje.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Crear un VSPackage

1. Cree un proyecto VSIX denominado **FirstPackage**. Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Cuando se abra el proyecto, agregue una plantilla de elementos de paquete de Visual Studio denominada **FirstPackage**. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >   y seleccione **paquete de Visual Studio**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *FirstPackage. CS*.

3. Compile la solución y comience la depuración.

    Aparece la instancia experimental de Visual Studio. Para obtener más información sobre la instancia experimental, vea [la instancia experimental](../extensibility/the-experimental-instance.md).

4. En la instancia experimental, abra la ventana **herramientas**  >  **extensiones y actualizaciones** . Debería ver la extensión **FirstPackage** aquí. (Si abre **extensiones y actualizaciones** en la instancia de trabajo de Visual Studio, no verá **FirstPackage**).

## <a name="load-the-vspackage"></a>Cargar el VSPackage

En este momento, la extensión no se carga porque no hay nada que provoque que se cargue. Por lo general, puede cargar una extensión cuando interactúe con su interfaz de usuario (al hacer clic en un comando de menú, abrir una ventana de herramientas) o especificando que el VSPackage debe cargarse en un contexto de interfaz de usuario específico. Para obtener más información sobre cómo cargar VSPackages y contextos de la interfaz de usuario, vea [cargar VSPackages](../extensibility/loading-vspackages.md). Para este procedimiento, le mostraremos cómo cargar un VSPackage cuando una solución está abierta.

1. Abra el archivo *FirstPackage. CS* . Busque la declaración de la `FirstPackage` clase. Reemplace los atributos existentes por los siguientes atributos:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Vamos a agregar un mensaje que nos permite saber que el VSPackage se ha cargado. Usamos el método del VSPackage `Initialize()` para hacerlo, porque solo puede obtener los servicios de Visual Studio una vez que se ha puesto en sitio el VSPackage. (Para obtener más información acerca de cómo obtener servicios, consulte [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)). Reemplace el `Initialize()` método de `FirstPackage` por el código que obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servicio, obtiene la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> método.

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

4. Abra una solución en la instancia experimental. Debería ver un cuadro de mensaje que indica el **primer paquete dentro de Initialize ()**.
