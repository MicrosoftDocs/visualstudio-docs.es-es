---
title: GetScheduledTasksForDebugger (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 648d48f34681865a34654ed9f82bd790d77b2395
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231169"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (Método)
Recupera una matriz de todas las tareas programadas.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en *mscorlib.dll*)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.  
  
## <a name="remarks"></a>Comentarios  
 Este método no es seguro para subprocesos y no debe usar simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler>. Llame a este método desde un depurador sólo cuando el depurador ha suspendido todos los demás subprocesos.  
  
## <a name="see-also"></a>Vea también  
 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)