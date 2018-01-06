---
title: Cargar VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5efc043ae6e88f3f7b3c989a2c37c0ff9f555dd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="loading-vspackages"></a>Cargar VSPackages
Paquetes VSPackage se carga en Visual Studio solo cuando se requiere su funcionalidad. Por ejemplo, un VSPackage se carga cuando Visual Studio usa un generador de proyectos o un servicio que implementa el VSPackage. Esta característica se denomina carga retrasada, que se usa siempre que sea posible mejorar el rendimiento.  
  
> [!NOTE]
>  Visual Studio puede determinar cierta información de VSPackage, por ejemplo, los comandos que ofrece un paquete VSPackage, sin necesidad de cargar el VSPackage.  
  
 VSPackages puede establecerse para cargar automáticamente en un contexto de usuario determinado (interfaz), por ejemplo, cuando se abre una solución. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Carga automática un VSPackage en un contexto específico  
  
-   Agregue el `ProvideAutoLoad` de atributo para los atributos de VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Ver los campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obtener una lista de los contextos de la interfaz de usuario y sus valores GUID.  
  
-   Establecer un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
-   Crear el VSPackage e iniciar la depuración.  
  
-   Cargar una solución o crear uno.  
  
     El VSPackage carga y se detiene en el punto de interrupción.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forzar un VSPackage para cargar  
 En algunas circunstancias puede tener un paquete VSPackage forzar que otro VSPackage que se va a cargar. Por ejemplo, un VSPackage ligero podría cargar un paquete VSPackage mayor en un contexto que no está disponible como un CMDUIContext.  
  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forzar que un paquete VSPackage para cargar.  
  
-   Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método de VSPackage que obliga a otro paquete de VS para cargar:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Cuando se inicializa el VSPackage, forzará `PackageToBeLoaded` para cargar.  
  
     Carga de fuerza no debe usarse para la comunicación de VSPackage. Use [Using y proporcionar servicios](../extensibility/using-and-providing-services.md) en su lugar.
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)
