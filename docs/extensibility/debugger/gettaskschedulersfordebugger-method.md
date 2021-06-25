---
description: Recupera una matriz de todos los objetos System.Threading.Tasks.TaskScheduler que están activos actualmente.
title: Método GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58cb913f5dbc729c297de8a34aa5dd4c3c99b48a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900920"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede acceder a este miembro interno desde la .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente en este objeto <xref:System.AppDomain> .

## <a name="remarks"></a>Observaciones
 Este método no es seguro para subprocesos y no debe usarlo simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> . Llame a este método desde un depurador solo cuando el depurador haya suspendido todos los demás subprocesos.

## <a name="see-also"></a>Consulta también
- [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
