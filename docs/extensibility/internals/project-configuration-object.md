---
title: Objeto de configuración del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706655"
---
# <a name="project-configuration-object"></a>Objeto de configuración del proyecto
El objeto de configuración de proyecto administra la presentación de la información de configuración en la interfaz de usuario.

 ![Configuración de proyecto de Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Páginas de propiedades de configuración del proyecto

 El proveedor de configuración del proyecto administra las configuraciones del proyecto. El entorno y otros paquetes, para obtener acceso y recuperar información sobre las configuraciones de un proyecto, llame a las interfaces asociadas al objeto del proveedor de configuración del proyecto.

> [!NOTE]
> No se pueden crear ni editar archivos de configuración de soluciones mediante programación. Se debe usar `DTE.SolutionBuilder`. Consulte [configuración de soluciones](../../extensibility/internals/solution-configuration.md) para obtener más información.

 Para publicar un nombre para mostrar que se va a usar en la interfaz de usuario de configuración, el proyecto debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , que devuelve una lista de `IVsCfg` punteros que puede usar para obtener los nombres para mostrar de la información de configuración y plataforma que se mostrarán en la interfaz de usuario del entorno. La configuración activa y la plataforma vienen determinadas por la configuración del proyecto almacenada en la configuración de soluciones activa. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método se puede utilizar para recuperar la configuración del proyecto activo.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Opcionalmente, el objeto se puede implementar en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objeto con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objeto para que pueda recuperar un `IVsProjectCfg2` objeto basado en el nombre de la configuración del proyecto canónico.

 Otra manera de proporcionar el entorno y otros proyectos con acceso a las configuraciones de proyecto es para que los proyectos proporcionen una implementación del `IVsCfgProvider2::GetCfgs` método para devolver uno o más objetos de configuración. Los proyectos también pueden implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , que hereda de `IVsProjectCfg` y, por tanto `IVsCfg` , de, para proporcionar información específica de la configuración. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> admite plataformas y funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.

> [!NOTE]
> Dado que Visual Studio ya no está limitado a dos tipos de configuración, el código que procesa las configuraciones no se debe escribir con suposiciones sobre el número de configuraciones, ni debe escribirse con la suposición de que un proyecto que solo tiene una configuración es necesariamente depuración o comercial. Esto hace que el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> y esté <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.

 Llamar a `QueryInterface` en el objeto devuelto por `IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2` . Si `IVsGetCfgProvider` no se encuentra llamando a `QueryInterface` en el `IVsProject3` objeto de proyecto, puede tener acceso al objeto de proveedor de configuración mediante una llamada a `QueryInterface` en el objeto de explorador raíz de la jerarquía para el objeto devuelto para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` o a través de un puntero al proveedor de configuración devuelto para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` proporciona principalmente acceso a objetos de administración de compilación, depuración e implementación, y permite a los proyectos disponer de la libertad de agrupar las salidas. Los métodos de `IVsProjectCfg` y `IVsProjectCfg2` se pueden usar para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> para administrar el proceso de compilación y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> punteros para los grupos de salida de una configuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admita aunque el número de salidas contenidas dentro de un grupo puede variar de una configuración a una configuración. Los grupos también deben tener la misma información de identificador (nombre canónico, nombre para mostrar e información de grupo) de la configuración a la configuración de un proyecto. Para obtener más información, vea [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

 Para habilitar la depuración, las configuraciones deben implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` es una interfaz opcional implementada por los proyectos para permitir que el depurador inicie una configuración y se implementa en el objeto de configuración con `IVsCfg` y `IVsProjectCfg` . El entorno lo llama cuando el usuario elige iniciar el depurador presionando F5.

 `ISpecifyPropertyPages` y `IDispatch` se usan junto con las páginas de propiedades para recuperar y Mostrar información dependiente de la configuración al usuario. Para obtener más información, vea [páginas de propiedades](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
- [Páginas de propiedades](../../extensibility/internals/property-pages.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
