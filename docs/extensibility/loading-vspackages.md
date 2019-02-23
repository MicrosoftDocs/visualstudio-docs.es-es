---
title: Carga de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9878fea72c83cd6a466f2743f44d3eddca0bdba7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702062"
---
# <a name="load-vspackages"></a>Cargar VSPackages
Los paquetes VSPackage se cargan en Visual Studio solo cuando su funcionalidad es necesaria. Por ejemplo, un VSPackage se carga cuando Visual Studio utiliza un generador de proyectos o un servicio que implementa el VSPackage. Esta característica se denomina la carga diferida, que se usa siempre que sea posible mejorar el rendimiento.

> [!NOTE]
>  Visual Studio puede determinar cierta información de VSPackage, como los comandos que ofrece un paquete VSPackage, sin tener que cargar el VSPackage.

 VSPackages puede establecerse para cargar automáticamente en un contexto de interfaz (IU) de usuario determinado, por ejemplo, cuando se abre una solución. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Cargar automáticamente un VSPackage en un contexto específico

-   Agregar el `ProvideAutoLoad` atributo a los atributos de VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Ver los campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obtener una lista de los contextos de interfaz de usuario y sus valores GUID.

-   Establecer un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.

-   Crear el VSPackage e iniciar la depuración.

-   Cargue una solución o cree uno.

     El VSPackage carga y se detiene en el punto de interrupción.

## <a name="force-a-vspackage-to-load"></a>Forzar un VSPackage para cargar
 En algunas circunstancias puede tener un VSPackage forzar que se puede cargar otro paquete VSPackage. Por ejemplo, un VSPackage ligero podría cargar un VSPackage en un contexto que no está disponible como un CMDUIContext más grande.

 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forzar la carga de un paquete VSPackage.

-   Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método del VSPackage que obliga a otro VSPackage para cargar:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Cuando se inicializa el VSPackage, forzará `PackageToBeLoaded` para cargar.

     Carga de fuerza no debe usarse para la comunicación de VSPackage. Use [uso y proporcionan servicios](../extensibility/using-and-providing-services.md) en su lugar.

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
