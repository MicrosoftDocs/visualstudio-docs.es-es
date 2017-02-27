---
title: "Consideraciones para descargar y volver a cargar proyectos anidados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos anidados, descarga y carga"
  - "proyectos [Visual Studio SDK], descarga y carga anidados"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Consideraciones para descargar y volver a cargar proyectos anidados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Al implementar tipos de proyecto anidados, debe realizar pasos adicionales cuando descarga y recarga los proyectos.  Correctamente para notificar a los agentes de escucha los eventos de la solución, debe correctamente provocar eventos de `OnBeforeUnloadProject` y de `OnAfterLoadProject` .  
  
 Una razón que debe provocar estos eventos de esta manera es que no desea que el control \(SCC\) de código fuente para eliminar elementos del servidor y agregarlos posteriores como algo nuevo si hay una operación de `Get` de SCC.  En ese caso, un nuevo archivo se carga fuera del SCC y tiene que descargar y recargar todos los archivos en caso de que son diferentes.  El SCC llama `ReloadItem`.  La implementación de esa llamada es eliminar el proyecto y volver a crearlo de nuevo implementando `IVsFireSolutionEvents` para llamar a `OnBeforeUnloadProject` y `OnAfterLoadProject`.  Al realizar esta implementación, el SCC recibe información que el proyecto se ha eliminado y agregado temporalmente de nuevo.  Por consiguiente, el SCC no funciona en el proyecto como si el proyecto fuera eliminado del servidor y después agregado realmente de nuevo.  
  
## recargar proyectos  
 Para admitir recargar de proyectos anidados, se implementa el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> .  En la implementación de `ReloadItem`, cierre los proyectos anidados y después se vuelve a crear.  
  
 Normalmente cuando se vuelve a cargar un proyecto, el IDE genera el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> y los eventos de `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` .  Sin embargo, para los proyectos anidados que se eliminarán y recargados, el proyecto principal inicia el proceso, no el IDE.  Dado que el proyecto principal no genera eventos de la solución, y el IDE no tiene información sobre la inicialización del proceso, los eventos no se provocan.  
  
 Para controlar este proceso, el proyecto principal llama `QueryInterface` en la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> .  `IVsFireSolutionEvents` tiene funciones que indican al IDE que provoque el evento de `OnBeforeUnloadProject` para descargar el proyecto anidadas, y después provoca el evento de `OnAfterLoadProject` recargar el mismo proyecto.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Proyectos de anidamiento](../../extensibility/internals/nesting-projects.md)