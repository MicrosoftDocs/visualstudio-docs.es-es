---
title: Consideraciones para descargar y recargar anidar proyectos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bfe39e82a9f15825a5328fe1950347add9d182bb
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Consideraciones para descargar y volver a cargar proyectos anidados

Al implementar los tipos de proyecto anidado, debe realizar pasos adicionales al descargar y volver a cargar los proyectos. Para notificar correctamente a los agentes de escucha de eventos de la solución, debe generar correctamente el `OnBeforeUnloadProject` y `OnAfterLoadProject` eventos.

Es una de las razones para generar estos eventos para el control de código fuente (SCC). No desea SCC para eliminar los elementos del servidor y, a continuación, agregarlos como *nueva* si hay un `Get` operación de control de código fuente. En ese caso, podría cargar un nuevo archivo fuera del control de código fuente. Deberá descargar y volver a cargar todos los archivos en caso de que sean diferentes.

Llamadas de control de código de origen `ReloadItem`. Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz para llamar a `OnBeforeUnloadProject` y `OnAfterLoadProject` para eliminar el proyecto y volver a crearla. Al implementar la interfaz de esta manera, SCC se informa de que el proyecto se ha eliminado y volverán a aparecer temporalmente. Por lo tanto, SCC no funciona en el proyecto como si fuera el proyecto *realmente* eliminado y vuelto a agregar.

## <a name="reloading-projects"></a>Volver a cargar proyectos

Para admitir la recarga de proyectos anidados, se implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. En la implementación de `ReloadItem`, cierre los proyectos anidados y, a continuación, volver a crearlos después.

Normalmente cuando se vuelve a cargar un proyecto, el IDE genera el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventos. Sin embargo, para los proyectos anidados se elimina y vuelve a cargar, el proyecto principal inicia el proceso, no el IDE. Dado que el proyecto principal no genera eventos de la solución y el IDE no tiene información sobre la inicialización del proceso, no se producen los eventos.

Para controlar este proceso, las llamadas de proyecto principal `QueryInterface` en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz. `IVsFireSolutionEvents` tiene funciones que indican el IDE para generar el `OnBeforeUnloadProject` eventos para descargar el proyecto anidado y, a continuación, generar el `OnAfterLoadProject` eventos para volver a cargar el mismo proyecto.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)