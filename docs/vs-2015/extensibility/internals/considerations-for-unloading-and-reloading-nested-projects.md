---
title: Consideraciones para descargar y recargar anidados proyectos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28c5ba7dffecd73556a5f963c471910bb190f1db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756972"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Consideraciones para descargar y volver a cargar proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al implementar los tipos de proyecto anidado, debe realizar pasos adicionales al descargar y cargar los proyectos. Para notificar correctamente los agentes de escucha de eventos de la solución, debe generar correctamente el `OnBeforeUnloadProject` y `OnAfterLoadProject` eventos.  
  
 Una razón que debe generar estos eventos de esta manera es que no desea control de código fuente (SCC) para eliminar los elementos del servidor y, a continuación, agregarlos como algo nuevo si hay un `Get` operación de control de código fuente. En ese caso, se cargan un nuevo archivo de SCC y tendrá que descargar y recargar todos los archivos en caso de que son diferentes. Las llamadas de SCC `ReloadItem`. La implementación de esa llamada es eliminar el proyecto y volver a crearla de nuevo mediante la implementación de `IVsFireSolutionEvents` para llamar a `OnBeforeUnloadProject` y `OnAfterLoadProject`. Al realizar esta implementación, el SCC se informa de que se eliminó temporalmente el proyecto y se puede agregar de nuevo. Por lo tanto, el SCC no funcionan en el proyecto como si el proyecto se ha eliminado realmente desde el servidor y, a continuación, puede agregar de nuevo.  
  
## <a name="reloading-projects"></a>Volver a cargar proyectos  
 Para admitir la recarga de proyectos anidados, implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. En la implementación de `ReloadItem`, cierre los proyectos anidados y, a continuación, volver a crearlos.  
  
 Normalmente, cuando se vuelve a cargar un proyecto, el IDE provoca la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> y `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventos. Sin embargo, para los proyectos anidados que se eliminará y se vuelve a cargar, el proyecto principal inicia el proceso, no el IDE. Dado que el proyecto principal no genera eventos de la solución y el IDE no tiene información sobre la inicialización del proceso, no se generan los eventos.  
  
 Para controlar este proceso, las llamadas de proyecto primario `QueryInterface` en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz desactivado el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfaz. `IVsFireSolutionEvents` tiene funciones que indican al IDE que elevar el `OnBeforeUnloadProject` eventos para descargar el proyecto anidado y, a continuación, genere el `OnAfterLoadProject` eventos para volver a cargar el mismo proyecto.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)

