---
title: Objeto de configuración del proyecto ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706655"
---
# <a name="project-configuration-object"></a>Objeto de configuración del proyecto
El objeto de configuración del proyecto administra la visualización de la información de configuración en la interfaz de usuario.

 ![Configuración del proyecto](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") de Visual Studio Páginas de propiedades de configuración del proyecto

 El proveedor de configuración del proyecto administra las configuraciones del proyecto. El entorno y otros paquetes, para obtener acceso y recuperar información sobre las configuraciones de un proyecto, llame a las interfaces adjuntas al objeto Proveedor de configuración del proyecto.

> [!NOTE]
> No puede crear ni editar archivos de configuración de solución mediante programación. Se debe usar `DTE.SolutionBuilder`. Consulte Configuración de la [solución](../../extensibility/internals/solution-configuration.md) para obtener más información.

 Para publicar un nombre para mostrar que se usará <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>en la interfaz de usuario de configuración, el proyecto debe implementar . El entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>llama , que `IVsCfg` devuelve una lista de punteros que puede usar para obtener los nombres para mostrar de la información de configuración y plataforma que se mostrará en la interfaz de usuario del entorno. La configuración activa y la plataforma están determinadas por la configuración del proyecto almacenada en la configuración de la solución activa. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método se puede utilizar para recuperar la configuración del proyecto activo.

 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> objeto se puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> opcionalmente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> en el objeto con `IVsProjectCfg2` el objeto para permitirle recuperar un objeto basado en el nombre de configuración del proyecto canónico.

 Otra forma de proporcionar el entorno y otros proyectos con acceso a `IVsCfgProvider2::GetCfgs` las configuraciones de proyecto es que los proyectos proporcionen una implementación del método para devolver uno o varios objetos de configuración. Los proyectos también <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>pueden implementar, `IVsProjectCfg` que hereda de y, por lo no, de `IVsCfg`, para proporcionar información específica de la configuración. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>admite plataformas y funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.

> [!NOTE]
> Dado que Visual Studio ya no está limitado a dos tipos de configuración, el código que procesa las configuraciones no debe escribirse con suposiciones sobre el número de configuraciones, ni debe escribirse con la suposición de que un proyecto que solo tiene una configuración es necesariamente Debug o Retail. Esto hace que <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> el uso y obsoleto.

 Llamar `QueryInterface` al objeto`IVsGetCfgProvider::GetCfgProvider` devuelto `IVsCfgProvider2`desde retrieves . Si `IVsGetCfgProvider` no se `QueryInterface` encuentra `IVsProject3` llamando al objeto de proyecto, puede `QueryInterface` tener acceso al objeto de `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`proveedor de configuración llamando al objeto `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`de explorador raíz de jerarquía para el objeto devuelto para , o a través de un puntero al proveedor de configuración devuelto para .

 `IVsProjectCfg2`principalmente proporciona acceso a objetos de administración de compilación, depuración e implementación y permite a los proyectos la libertad de agrupar las salidas. Los `IVsProjectCfg` métodos `IVsProjectCfg2` y se <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> pueden usar para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> para administrar el proceso de compilación y punteros para los grupos de salida de una configuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admite aunque el número de salidas contenidas en un grupo puede variar de una configuración a otra. Los grupos también deben tener la misma información de identificador (nombre canónico, nombre para mostrar e información de grupo) desde la configuración hasta la configuración dentro de un proyecto. Para obtener más información, consulte [Configuración del proyecto para salida](../../extensibility/internals/project-configuration-for-output.md).

 Para habilitar la depuración, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>las configuraciones deben implementar . `IVsDebuggableProjectCfg`es una interfaz opcional implementada por los proyectos para permitir que el `IVsCfg` depurador `IVsProjectCfg`inicie una configuración y se implementa en el objeto de configuración con y . El entorno lo llama cuando el usuario elige iniciar el depurador presionando F5.

 `ISpecifyPropertyPages`y `IDispatch` se utilizan junto con las páginas de propiedades para recuperar y mostrar información dependiente de la configuración al usuario. Para obtener más información, vea [Páginas](../../extensibility/internals/property-pages.md)de propiedades .

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
- [Páginas de propiedades](../../extensibility/internals/property-pages.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
