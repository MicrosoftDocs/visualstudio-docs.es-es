---
title: Cargando VSPackages | Microsoft Docs
description: Obtenga información sobre cómo cargar VSPackages en Visual Studio, incluida la carga retrasada, que se usa siempre que sea posible para mejorar el rendimiento.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0aeab78a2f64be2df6f601ad8ed224f13071eb8c
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616109"
---
# <a name="load-vspackages"></a>Cargar VSPackages
Los VSPackages se cargan en Visual Studio solo cuando se requiere su funcionalidad. Por ejemplo, un VSPackage se carga cuando Visual Studio usa un generador de proyectos o un servicio que implementa el VSPackage. Esta característica se denomina carga retrasada, que se usa siempre que sea posible para mejorar el rendimiento.

> [!NOTE]
> Visual Studio puede determinar determinada información de VSPackage, como los comandos que ofrece un VSPackage, sin cargar el VSPackage.

 Los VSPackages se pueden configurar para que se carguen en un contexto de interfaz de usuario determinado, por ejemplo, cuando se abre una solución. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Cargar autocarga de un VSPackage en un contexto específico

- Agregue el `ProvideAutoLoad` atributo a los atributos de VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Vea los campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obtener una lista de los contextos de la interfaz de usuario y sus valores GUID.

- Establezca un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.

- Compile el VSPackage e inicie la depuración.

- Cargue una solución o cree una.

     El VSPackage se carga y se detiene en el punto de interrupción.

## <a name="force-a-vspackage-to-load"></a>Forzar la carga de un VSPackage
 En algunas circunstancias, es posible que un VSPackage tenga que forzar la carga de otro VSPackage. Por ejemplo, un VSPackage ligero podría cargar un VSPackage mayor en un contexto que no está disponible como CMDUIContext.

 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forzar la carga de un VSPackage.

- Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método del VSPackage que fuerza la carga de otro VSPackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Cuando se inicializa el VSPackage, se forzará la `PackageToBeLoaded` carga.

     La carga forzada no debe usarse para la comunicación de VSPackage. Use [y proporcione servicios](../extensibility/using-and-providing-services.md) en su lugar.

## <a name="see-also"></a>Consulte también
- [VSPackages](../extensibility/internals/vspackages.md)
