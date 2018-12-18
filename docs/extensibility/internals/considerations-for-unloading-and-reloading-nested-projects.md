---
title: Consideraciones para descargar y recargar anidados proyectos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c38b50f661ed7ea16c56d9a877b809d2d60dd51c
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513463"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Consideraciones para descargar y recargar proyectos anidados

Al implementar los tipos de proyecto anidado, debe realizar pasos adicionales al descargar y cargar los proyectos. Para notificar correctamente los agentes de escucha de eventos de la solución, debe generar correctamente el `OnBeforeUnloadProject` y `OnAfterLoadProject` eventos.

Es uno de los motivos para generar estos eventos para el control de código fuente (SCC). No desea SCC para eliminar los elementos del servidor y, a continuación, agregarlos como *nueva* si hay un `Get` operación de control de código fuente. En ese caso, se podría cargar un nuevo archivo de SCC. Deberá descargar y recargar todos los archivos en caso de que son diferentes.

Las llamadas de control de código de origen `ReloadItem`. Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz para llamar a `OnBeforeUnloadProject` y `OnAfterLoadProject` para eliminar el proyecto y volver a crearla. Al implementar la interfaz de este modo, SCC se informa de que se eliminó temporalmente el proyecto y se puede agregar de nuevo. Por lo tanto, control de código fuente no funciona en el proyecto como si fuera el proyecto *realmente* elimina y vuelve a agregar.

## <a name="reload-projects"></a>Vuelva a cargar proyectos

Para admitir la recarga de proyectos anidados, implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. En la implementación de `ReloadItem`, cierre los proyectos anidados y, a continuación, volver a crearlos.

Normalmente, cuando se vuelve a cargar un proyecto, el IDE provoca la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventos. Sin embargo, para los proyectos anidados que se elimina y vuelve a cargar, el proyecto principal inicia el proceso, no el IDE. Dado que el proyecto principal no genera eventos de la solución y el IDE no tiene información sobre la inicialización del proceso, no se generan los eventos.

Para controlar este proceso, las llamadas de proyecto primario `QueryInterface` en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaz. `IVsFireSolutionEvents` tiene funciones que indican al IDE que elevar el `OnBeforeUnloadProject` eventos para descargar el proyecto anidado y, a continuación, genere el `OnAfterLoadProject` eventos para volver a cargar el mismo proyecto.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Proyectos de anidamiento](../../extensibility/internals/nesting-projects.md)