---
title: TASK_STATE_CANCELED (campo) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 869553b18f16135fe81d1a33e64eba1d33f0990b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577190"
---
# <a name="taskstatecanceled-field"></a>TASK_STATE_CANCELED (Campo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [TASK_STATE_CANCELED (campo)](https://docs.microsoft.com/visualstudio/extensibility/debugger/task-state-canceled-field).  
  
La tarea se canceló antes de que ha alcanzado el estado de ejecución, o se confirma su cancelación y completado sin excepciones.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## <a name="remarks"></a>Comentarios  
 Si el [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene este valor, el <xref:System.Threading.Tasks.Task.Status%2A> propiedad devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vea también  
 [Clase Task](../../extensibility/debugger/task-class-internal-members.md)

