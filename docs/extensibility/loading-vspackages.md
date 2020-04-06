---
title: Carga de VSPackages ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702965"
---
# <a name="load-vspackages"></a>Cargar VSPackages
VSPackages se cargan en Visual Studio solo cuando se requiere su funcionalidad. Por ejemplo, un VSPackage se carga cuando Visual Studio usa un generador de proyectos o un servicio que implementa el VSPackage. Esta característica se denomina carga retrasada, que se utiliza siempre que sea posible para mejorar el rendimiento.

> [!NOTE]
> Visual Studio puede determinar cierta información de VSPackage, como los comandos que ofrece un VSPackage, sin cargar el VSPackage.

 VSPackages se puede establecer para cargar automáticamente en un contexto de interfaz de usuario (UI) determinado, por ejemplo, cuando una solución está abierta. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Cargar automáticamente un VSPackage en un contexto específico

- Agregue `ProvideAutoLoad` el atributo a los atributos de VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Consulte los campos <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> enumerados de para obtener una lista de los contextos de interfaz de usuario y sus valores GUID.

- Establezca un punto <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> de interrupción en el método.

- Compile el VSPackage e inicie la depuración.

- Cargue una solución o cree una.

     El VSPackage se carga y se detiene en el punto de interrupción.

## <a name="force-a-vspackage-to-load"></a>Forzar un VSPackage para cargar
 En algunas circunstancias, un VSPackage puede tener que forzar otro VSPackage para cargar. Por ejemplo, un VSPackage ligero podría cargar un VSPackage más grande en un contexto que no está disponible como CMDUIContext.

 Puede usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> el método para forzar un VSPackage para cargar.

- Inserte este código <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> en el método del VSPackage que obliga a otro VSPackage a cargar:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Cuando se inicializa el VSPackage, `PackageToBeLoaded` forzará a cargar.

     Forzar la carga no se debe usar para la comunicación de VSPackage. Utilice [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md) en su lugar.

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
