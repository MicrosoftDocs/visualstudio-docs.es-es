---
title: Project Configuration Object | Microsoft Docs
description: Obtenga información sobre cómo el objeto de configuración del proyecto administra la presentación de información de configuración en la interfaz de usuario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 15a999f78d017c76ee021f86d81cb611310d079d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899867"
---
# <a name="project-configuration-object"></a>Objeto de configuración del proyecto
El objeto de configuración del proyecto administra la presentación de información de configuración en la interfaz de usuario.

 ![Visual Studio project configuration](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Páginas de propiedades de configuración del proyecto

 El proveedor de configuración de proyectos administra las configuraciones del proyecto. El entorno y otros paquetes, para obtener acceso a y recuperar información sobre las configuraciones de un proyecto, llame a las interfaces adjuntas al objeto proveedor de configuración de proyecto.

> [!NOTE]
> No se pueden crear ni editar archivos de configuración de soluciones mediante programación. Se debe usar `DTE.SolutionBuilder`. Consulte [Configuración de la](../../extensibility/internals/solution-configuration.md) solución para obtener más información.

 Para publicar un nombre para mostrar que se usará en la interfaz de usuario de configuración, el proyecto debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . El entorno llama a , que devuelve una lista de punteros que puede usar para obtener los nombres para mostrar de la información de configuración y plataforma que se mostrará en la interfaz de usuario <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> `IVsCfg` del entorno. La configuración activa y la plataforma están determinadas por la configuración del proyecto almacenada en la configuración de la solución activa. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método se puede usar para recuperar la configuración activa del proyecto.

 Opcionalmente, el objeto se puede implementar en el objeto con el objeto para permitirle recuperar un objeto basado en el nombre de configuración <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> canónica del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> `IVsProjectCfg2` proyecto.

 Otra manera de proporcionar el entorno y otros proyectos con acceso a las configuraciones de proyecto es que los proyectos proporcionen una implementación del método para devolver `IVsCfgProvider2::GetCfgs` uno o varios objetos de configuración. Los proyectos también pueden implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , que hereda de y, por `IVsProjectCfg` tanto, de , para proporcionar información `IVsCfg` específica de la configuración. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> admite plataformas y funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.

> [!NOTE]
> Puesto que Visual Studio ya no se limita a dos tipos de configuración, el código que procesa las configuraciones no debe escribirse con suposiciones sobre el número de configuraciones, ni debe escribirse con la suposición de que un proyecto que tiene solo una configuración es necesariamente Debug o Retail. Esto hace que el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> sea obsoleto.

 Al `QueryInterface` llamar a en el objeto devuelto desde se recupera `IVsGetCfgProvider::GetCfgProvider` `IVsCfgProvider2` . Si no se encuentra llamando al objeto de proyecto, puede acceder al objeto del proveedor de configuración mediante una llamada a en el objeto del explorador raíz de jerarquía para el objeto devuelto para , o a través de un puntero al proveedor de configuración devuelto `IVsGetCfgProvider` `QueryInterface` para `IVsProject3` `QueryInterface` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` proporciona principalmente acceso a los objetos de administración de compilación, depuración e implementación y permite a los proyectos la libertad de agrupar salidas. Los métodos de y se pueden usar para implementar para administrar el proceso de compilación `IVsProjectCfg` `IVsProjectCfg2` y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> punteros para los grupos de salida de una configuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admita, aunque el número de salidas contenidas en un grupo puede variar de una configuración a otra. Los grupos también deben tener la misma información de identificador (nombre canónico, nombre para mostrar e información de grupo) desde la configuración a la configuración dentro de un proyecto. Para obtener más información, vea [Configuración del proyecto para la salida.](../../extensibility/internals/project-configuration-for-output.md)

 Para habilitar la depuración, las configuraciones deben implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` es una interfaz opcional implementada por proyectos para permitir que el depurador inicie una configuración y se implementa en el objeto de configuración con `IVsCfg` y `IVsProjectCfg` . El entorno lo llama cuando el usuario decide iniciar el depurador presionando F5.

 `ISpecifyPropertyPages` y se usan junto con las páginas de propiedades para recuperar y mostrar información `IDispatch` dependiente de la configuración al usuario. Para obtener más información, vea [Páginas de propiedades](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Consulta también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
- [Páginas de propiedades](../../extensibility/internals/property-pages.md)
- [Configuración de la solución](../../extensibility/internals/solution-configuration.md)
