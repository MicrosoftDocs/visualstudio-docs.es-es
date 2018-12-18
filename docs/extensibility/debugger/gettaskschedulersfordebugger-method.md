---
title: GetTaskSchedulersForDebugger (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dc8e43629eab80dc3164813d0b8d0f380e8f86a
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231192"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
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
 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)