---
title: "Objeto de configuración de proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f9bfae4fb64a4dde27f8156560f0fa850fcd5885
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-object"></a>Objeto de configuración de proyecto
El objeto de configuración de proyecto administra la presentación de información de configuración de la interfaz de usuario.  
  
 ![Configuración de proyecto de Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Páginas de propiedades de configuración de proyecto  
  
 El proveedor de configuración de proyecto administra las configuraciones de proyecto. El entorno y otros paquetes, para obtener acceso y recuperar información acerca de las configuraciones del proyecto, llame a las interfaces que se adjunta al objeto de proveedor de configuración de proyecto.  
  
> [!NOTE]
>  No se puede crear o editar archivos de configuración de la solución mediante programación. Debe usar `DTE.SolutionBuilder`. Vea [configuración de la solución](../../extensibility/internals/solution-configuration.md) para obtener más información.  
  
 Para publicar un nombre para mostrar que se usará en la configuración de la interfaz de usuario, debe implementar el proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. El entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, que devuelve una lista de `IVsCfg` punteros que puede usar para obtener los nombres para mostrar para la información de configuración y plataforma se muestre en la interfaz de usuario del entorno. La plataforma y la configuración activa dependen de la configuración del proyecto almacenada en la configuración de soluciones activas. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método se puede utilizar para recuperar la configuración del proyecto activo.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> objeto opcionalmente se puede implementar en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objeto con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objeto para que pueda recuperar una `IVsProjectCfg2` objeto basado en el nombre de la configuración de proyecto canónica.  
  
 Es otra manera de proporcionar el entorno y otros proyectos con acceso a las configuraciones de proyecto para que los proyectos proporcionar una implementación de la `IVsCfgProvider2::GetCfgs` método para devolver uno o varios objetos de configuración. También pueden implementar los proyectos <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, que hereda de `IVsProjectCfg` y, por tanto, de `IVsCfg`, para proporcionar información específica de la configuración. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>admite plataformas y la funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.  
  
> [!NOTE]
>  Dado que Visual Studio ya no está limitado a dos tipos de configuración, el código que procesa las configuraciones no debe escribirse con suposiciones sobre el número de configuraciones ni deben escribirse con la suposición de que un proyecto que tiene solo uno configuración es necesariamente depuración o minorista. Esto hace que el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleta.  
  
 Al llamar a `QueryInterface` en el objeto devuelto desde`IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Si `IVsGetCfgProvider` no se encuentra mediante una llamada a `QueryInterface` en el `IVsProject3` objeto de proyecto, tener acceso al objeto de proveedor de configuración mediante una llamada a `QueryInterface` en el objeto de explorador raíz de jerarquía para el objeto devuelto para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, o a través un puntero para el proveedor de configuración que se devuelve para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2`principalmente proporciona acceso a compilar, depurar y objetos de administración de implementación y permite la libertad de salidas de grupo de proyectos. Los métodos de `IVsProjectCfg` y `IVsProjectCfg2` puede utilizarse para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> para administrar el proceso de compilación, y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> punteros para los grupos de resultados de una configuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que admite, aunque el número de salidas dentro de un grupo puede variar para cada configuración. Los grupos también deben tener la misma información de identificador (nombre canónico, nombre para mostrar y obtener información de grupo) de configuración dentro de un proyecto. Para obtener más información, consulte [configuración del proyecto para la salida de](../../extensibility/internals/project-configuration-for-output.md).  
  
 Para habilitar la depuración, deben implementar las configuraciones de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg`es una interfaz opcional que implementa los proyectos para permitir que el depurador para iniciar una configuración y se implementa en el objeto de configuración con `IVsCfg` y `IVsProjectCfg`. El entorno llama cuando el usuario elige iniciar al depurador presionando F5.  
  
 `ISpecifyPropertyPages`y `IDispatch` se usan junto con páginas de propiedades para recuperar y mostrar información dependiendo de la configuración para el usuario. Para obtener más información, consulte [páginas de propiedades](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para una compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)   
 [Páginas de propiedades](../../extensibility/internals/property-pages.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)