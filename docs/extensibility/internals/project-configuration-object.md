---
title: "Objeto de configuraci&#243;n de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "las configuraciones de proyecto, objeto"
  - "objetos de configuración de proyecto"
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Objeto de configuraci&#243;n de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El objeto de configuración de proyecto administra la presentación de información de configuración de la interfaz de usuario.  
  
 ![Configuración de proyectos de Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Páginas de propiedades de configuración de proyecto  
  
 El proveedor de configuración de proyecto administra las configuraciones del proyecto. El entorno y otros paquetes, para obtener acceso y recuperar información acerca de las configuraciones de un proyecto, llame a las interfaces que se adjunta al objeto de proveedor de configuración de proyecto.  
  
> [!NOTE]
>  No se puede crear o editar archivos de configuración de la solución mediante programación. Debe usar `DTE.SolutionBuilder`. Vea [Configuración de soluciones](../../extensibility/internals/solution-configuration.md) para obtener más información.  
  
 Para publicar un nombre para mostrar que se utilizará en la interfaz de usuario de configuración, debe implementar el proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. El entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, que devuelve una lista de `IVsCfg` punteros que puede usar para obtener los nombres para mostrar para la información de configuración y plataforma que se mostrarán en la interfaz de usuario del entorno. La configuración activa y la plataforma se determinan mediante la configuración del proyecto almacenada en la configuración de soluciones activas. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método puede utilizarse para recuperar la configuración del proyecto activo.  
  
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> objeto opcionalmente puede implementarse en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> de objeto con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objeto para que pueda recuperar una `IVsProjectCfg2` objeto basado en el nombre de la configuración de proyecto canónico.  
  
 Es otra manera de proporcionar el entorno y otros proyectos con acceso a las configuraciones de proyecto para que los proyectos proporcionar una implementación de la `IVsCfgProvider2::GetCfgs` que devuelva uno o varios objetos de configuración. También pueden implementar los proyectos <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, que se deriva de `IVsProjectCfg` y, por tanto, desde `IVsCfg`, para proporcionar información específica de la configuración.<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> admite plataformas y funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.  
  
> [!NOTE]
>  Dado que Visual Studio ya no está limitado a dos tipos de configuración, el código que procesa las configuraciones no debe escribirse con suposiciones acerca del número de configuraciones, ni se debe escribir con la suposición de que un proyecto que tiene una sola configuración es necesariamente comercial o depuración. Esto hace que el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleta.  
  
 Llamar a `QueryInterface` en el objeto devuelto desde`IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Si `IVsGetCfgProvider` no se encuentra mediante una llamada a `QueryInterface` en la `IVsProject3` objeto de proyecto, tener acceso al objeto de proveedor de configuración mediante una llamada a `QueryInterface` en el objeto de explorador raíz de jerarquía para el objeto devuelto para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, o a través de un puntero a devolver para el proveedor de configuración `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` principalmente, proporciona acceso a compilar, depurar y objetos de administración de la implementación y permite la libertad de salidas del grupo de proyectos. Los métodos de `IVsProjectCfg` y `IVsProjectCfg2` pueden utilizar para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> para administrar el proceso de compilación y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> punteros para los grupos de resultados de una configuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que admite incluso aunque el número de salidas dentro de un grupo puede variar para cada configuración. Los grupos también deben tener la misma información de identificador \(nombre canónico, información de grupo y nombre para mostrar\) de configuración dentro de un proyecto. Para obtener más información, consulta [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).  
  
 Para habilitar la depuración, deben implementar las configuraciones de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.`IVsDebuggableProjectCfg` es una interfaz opcional que implementa los proyectos para permitir que el depurador para iniciar una configuración y se implementa en el objeto de configuración con `IVsCfg` y `IVsProjectCfg`. El entorno llama cuando el usuario decide iniciar al depurador presionando F5.  
  
 `ISpecifyPropertyPages` y `IDispatch` se usan junto con las páginas de propiedades para recuperar y mostrar información dependiendo de la configuración para el usuario. Para obtener más información, consulta [Páginas de propiedades](../../extensibility/internals/property-pages.md).  
  
## Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)   
 [Páginas de propiedades](../../extensibility/internals/property-pages.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)