---
title: Consideraciones para descargar y volver a cargar proyectos anidados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197012"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Consideraciones para descargar y volver a cargar proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al implementar tipos de proyecto anidados, debe realizar pasos adicionales al descargar y volver a cargar los proyectos. Para notificar correctamente a los agentes de escucha los eventos de la solución, debe generar correctamente los `OnBeforeUnloadProject` `OnAfterLoadProject` eventos y.  
  
 Una razón por la que debe generar estos eventos de esta manera es que no desea que el control de código fuente (SCC) elimine los elementos del servidor y, a continuación, los vuelva a agregar como algo nuevo si hay una `Get` operación de SCC. En ese caso, un archivo nuevo se cargará fuera de SCC y tendrá que descargar y volver a cargar todos los archivos en caso de que sean diferentes. Llamadas de SCC `ReloadItem` . La implementación de esa llamada es eliminar el proyecto y volver a crearlo implementando `IVsFireSolutionEvents` para llamar a `OnBeforeUnloadProject` y `OnAfterLoadProject` . Al realizar esta implementación, se informa al SCC de que el proyecto se eliminó temporalmente y se agregó de nuevo. Por consiguiente, el SCC no funciona en el proyecto como si el proyecto se eliminara realmente del servidor y, a continuación, se vuelve a agregar.  
  
## <a name="reloading-projects"></a>Volver a cargar proyectos  
 Para admitir la recarga de proyectos anidados, se implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. En la implementación de `ReloadItem` , se cierran los proyectos anidados y, a continuación, se vuelven a crear.  
  
 Normalmente, cuando se recarga un proyecto, el IDE genera los <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventos y. Sin embargo, en el caso de los proyectos anidados que se van a eliminar y recargar, el proyecto primario inicia el proceso, no el IDE. Dado que el proyecto primario no genera eventos de la solución y el IDE no tiene información sobre la inicialización del proceso, no se generan los eventos.  
  
 Para controlar este proceso, el proyecto primario llama a `QueryInterface` en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz fuera de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfaz. `IVsFireSolutionEvents` tiene funciones que indican al IDE que genere el `OnBeforeUnloadProject` evento para descargar el proyecto anidado y, a continuación, genere el `OnAfterLoadProject` evento para volver a cargar el mismo proyecto.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
