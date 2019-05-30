---
title: GetTaskSchedulersForDebugger (método) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8d038c8c67731fe1bff9ec705b5ddf416807a57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353721"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están actualmente activos en este <xref:System.AppDomain>.

## <a name="remarks"></a>Comentarios
 Este método no es seguro para subprocesos y no debe usar simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler>. Llame a este método desde un depurador sólo cuando el depurador ha suspendido todos los demás subprocesos.

## <a name="see-also"></a>Vea también
- [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)