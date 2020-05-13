---
title: Consideraciones para la descarga y recarga de proyectos anidados Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709291"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Consideraciones para descargar y recargar proyectos anidados

Al implementar tipos de proyecto anidados, debe realizar pasos adicionales al descargar y volver a cargar los proyectos. Para notificar correctamente a los agentes de `OnBeforeUnloadProject` `OnAfterLoadProject` escucha a los eventos de la solución, debe generar correctamente los eventos y.

Una razón para generar estos eventos es para el control de código fuente (SCC). No desea que SCC elimine los elementos del servidor y, a continuación, vuelva a agregarlos como *nuevos* si hay una operación `Get` de SCC. En ese caso, un nuevo archivo se cargaría fuera de SCC. Tendrías que descargar y volver a cargar todos los archivos en caso de que sean diferentes.

El control `ReloadItem`de código fuente llama . Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> la interfaz para llamar `OnBeforeUnloadProject` y `OnAfterLoadProject` eliminar el proyecto y volver a crearlo. Al implementar la interfaz de esta manera, se informa a SCC de que el proyecto se eliminó temporalmente y se volvió a agregar. Por lo tanto, SCC no funciona en el proyecto como si el proyecto *se* eliminara y se hubiera reagregado realmente.

## <a name="reload-projects"></a>Recargar proyectos

Para admitir la recarga de proyectos <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> anidados, implemente el método. En la `ReloadItem`implementación de , se cierran los proyectos anidados y, a continuación, se vuelven a crear.

Normalmente, cuando se vuelve a cargar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> proyecto, el IDE genera los eventos y. Sin embargo, para los proyectos anidados que se eliminan y se vuelven a cargar, el proyecto primario inicia el proceso, no el IDE. Dado que el proyecto primario no genera eventos de solución y el IDE no tiene información sobre la inicialización del proceso, no se generan los eventos.

Para controlar este proceso, `QueryInterface` el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> proyecto primario llama a la interfaz. `IVsFireSolutionEvents`tiene funciones que indican al `OnBeforeUnloadProject` IDE que genere el evento `OnAfterLoadProject` para descargar el proyecto anidado y, a continuación, genere el evento para volver a cargar el mismo proyecto.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Proyectos Nest](../../extensibility/internals/nesting-projects.md)
