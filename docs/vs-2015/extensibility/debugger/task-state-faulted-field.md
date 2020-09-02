---
title: TASK_STATE_FAULTED campo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d659d31de221d7a08ee85bee6350ade5c5a95808
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176724"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED (Campo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La tarea se completó debido a una excepción no controlada.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## <a name="remarks"></a>Observaciones  
 Si el campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene este valor, la <xref:System.Threading.Tasks.Task.Status%2A> propiedad devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Consulte también  
 [Task (clase)](../../extensibility/debugger/task-class-internal-members.md)
