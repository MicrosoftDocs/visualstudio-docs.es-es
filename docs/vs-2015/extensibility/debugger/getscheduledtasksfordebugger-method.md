---
title: Método GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4ac6fa753be7672f1e698bda231bd11217c10d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152733"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (Método)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una matriz de todas las tareas programadas.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.  
  
## <a name="remarks"></a>Comentarios  
 Este método no es seguro para subprocesos y no debe usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> que se debe llamar desde un depurador solo cuando el depurador ha suspendido todos los demás subprocesos.  
  
## <a name="see-also"></a>Consulte también  
 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
