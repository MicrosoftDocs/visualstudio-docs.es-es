---
title: Consideraciones para descargar y recargar anidar proyectos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf34a3fe708a6ecab200262224da395b9fa37ecb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Consideraciones para descargar y volver a cargar proyectos anidados
Al implementar los tipos de proyecto anidado, debe realizar pasos adicionales al descargar y volver a cargar los proyectos. Para notificar correctamente a los agentes de escucha de eventos de la solución, debe generar correctamente el `OnBeforeUnloadProject` y `OnAfterLoadProject` eventos.  
  
 Una razón debe provocar estos eventos de esta manera es que no desea control de código fuente (SCC) para eliminar los elementos del servidor y, a continuación, agregarlos como algo nuevo si no hay un `Get` operación de control de código fuente. En ese caso, se puede cargar un nuevo archivo fuera del control de código fuente y tendrá que descargar y volver a cargar todos los archivos en caso de que son diferentes. Llamadas de SCC `ReloadItem`. La implementación de esa llamada consiste en eliminar el proyecto y volver a crearla de nuevo mediante la implementación `IVsFireSolutionEvents` para llamar a `OnBeforeUnloadProject` y `OnAfterLoadProject`. Al llevar a cabo esta implementación, el SCC se le informará de que el proyecto se ha eliminado y volverán a aparecer temporalmente. Por lo tanto, el SCC no funciona en el proyecto como si el proyecto se eliminan realmente desde el servidor y, a continuación, agregar de nuevo.  
  
## <a name="reloading-projects"></a>Volver a cargar proyectos  
 Para admitir la recarga de proyectos anidados, se implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. En la implementación de `ReloadItem`, cierre los proyectos anidados y, a continuación, volver a crearlos después.  
  
 Normalmente cuando se vuelve a cargar un proyecto, el IDE genera el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> y `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventos. Sin embargo, para los proyectos anidados se eliminará y se vuelve a cargar, el proyecto principal inicia el proceso, no el IDE. Dado que el proyecto principal no genera eventos de la solución y el IDE no tiene información sobre la inicialización del proceso, no se producen los eventos.  
  
 Para controlar este proceso, las llamadas de proyecto principal `QueryInterface` en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz desactivar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfaz. `IVsFireSolutionEvents`tiene funciones que indican el IDE para generar el `OnBeforeUnloadProject` eventos para descargar el proyecto anidado y, a continuación, generar el `OnAfterLoadProject` eventos para volver a cargar el mismo proyecto.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)