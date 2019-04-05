---
title: Objeto de configuración de proyecto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d84dd905c09b0bcc19833198b925f66dea245b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996362"
---
# <a name="project-configuration-object"></a>Objeto de configuración del proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El objeto de configuración de proyecto administra la presentación de información de configuración de la interfaz de usuario.  
  
 ![Configuración de proyecto de Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Páginas de propiedades de configuración de proyecto  
  
 El proveedor de configuración de proyecto administra las configuraciones de proyecto. El entorno y otros paquetes, para obtener acceso y recuperar información sobre las configuraciones de un proyecto, llame a las interfaces que se adjunta al objeto de proveedor de configuración de proyecto.  
  
> [!NOTE]
>  No se puede crear o editar archivos de configuración de la solución mediante programación. Debe usar `DTE.SolutionBuilder`. Consulte [configuración de la solución](../../extensibility/internals/solution-configuration.md) para obtener más información.  
  
 Para publicar un nombre para mostrar que se usará en la configuración de la interfaz de usuario, debe implementar el proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, que devuelve una lista de `IVsCfg` punteros que puede usar para obtener los nombres para mostrar para la información de configuración y plataforma que se mostrarán en la interfaz de usuario del entorno. La configuración activa y la plataforma se determinan mediante la configuración del proyecto almacenada en la configuración de soluciones activas. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método puede utilizarse para recuperar la configuración del proyecto activo.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> , opcionalmente, se puede implementar el objeto en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objeto con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objeto para que pueda recuperar un `IVsProjectCfg2` objeto según el nombre de la configuración de proyecto canónico.  
  
 Es otra manera de proporcionar el entorno y otros proyectos con acceso a las configuraciones de proyecto para que los proyectos proporcionar una implementación de la `IVsCfgProvider2::GetCfgs` método para devolver uno o más objetos de configuración. También pueden implementar los proyectos <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, que hereda de `IVsProjectCfg` y, por tanto, desde `IVsCfg`, para proporcionar información específica de la configuración. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> es compatible con plataformas y funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.  
  
> [!NOTE]
>  Dado que Visual Studio ya no se limita a dos tipos de configuración, no se debe escribir código que procesa las configuraciones con suposiciones sobre el número de configuraciones, ni debe escribirse con la suposición de que un proyecto que sólo tiene una configuración es necesariamente comercial o depuración. Esto hace que el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.  
  
 Una llamada a `QueryInterface` en el objeto devuelto desde`IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Si `IVsGetCfgProvider` no se encuentra mediante una llamada a `QueryInterface` en el `IVsProject3` objeto de proyecto, puede tener acceso el objeto de proveedor de configuración mediante una llamada a `QueryInterface` en el objeto de explorador raíz de jerarquía para el objeto devuelto para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, o a través un puntero a devolver para el proveedor de configuración `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` principalmente proporciona acceso a compilar, depurar y objetos de administración de implementación y permite a los proyectos de la libertad de salidas de grupo. Los métodos de `IVsProjectCfg` y `IVsProjectCfg2` puede utilizarse para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> para administrar el proceso de compilación y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> punteros para los grupos de salida de una configuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que admite, aunque el número de salidas contenida dentro de un grupo puede variar para cada configuración. Los grupos también deben tener la misma información de identificador (nombre canónico, nombre para mostrar y obtener información de grupo) de configuración dentro de un proyecto. Para obtener más información, consulte [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).  
  
 Para habilitar la depuración, deben implementar las configuraciones de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` es una interfaz opcional implementada por proyectos para permitir que el depurador para iniciar una configuración y se implementa en el objeto de configuración con `IVsCfg` y `IVsProjectCfg`. El entorno llama cuando el usuario elige iniciar al depurador presionando F5.  
  
 `ISpecifyPropertyPages` y `IDispatch` se usan junto con las páginas de propiedades para recuperar y mostrar información dependiente de la configuración para el usuario. Para obtener más información, consulte [páginas de propiedades](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Vea también  
 [Administración de las opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)   
 [Páginas de propiedades](../../extensibility/internals/property-pages.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
