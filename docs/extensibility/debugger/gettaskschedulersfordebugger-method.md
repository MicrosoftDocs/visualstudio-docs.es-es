---
title: GetTaskSchedulersForDebugger (Método) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738647"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
Recupera una matriz <xref:System.Threading.Tasks.TaskScheduler> de todos los objetos que están activos actualmente.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede tener acceso a este miembro interno desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Matriz de <xref:System.Threading.Tasks.TaskScheduler> todos los objetos <xref:System.AppDomain>que están activos actualmente en este archivo .

## <a name="remarks"></a>Observaciones
 Este método no es seguro para subprocesos y no debe <xref:System.Threading.Tasks.TaskScheduler>usarlo simultáneamente con otras instancias de . Llame a este método desde un depurador solo cuando el depurador haya suspendido todos los demás subprocesos.

## <a name="see-also"></a>Vea también
- [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
