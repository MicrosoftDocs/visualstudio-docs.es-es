---
title: Método GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738647"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente en este objeto <xref:System.AppDomain> .

## <a name="remarks"></a>Observaciones
 Este método no es seguro para subprocesos y no se debe utilizar simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> . Llame a este método desde un depurador solo cuando el depurador haya suspendido todos los demás subprocesos.

## <a name="see-also"></a>Vea también
- [TaskScheduler (clase)](../../extensibility/debugger/taskscheduler-class-internal-members.md)
