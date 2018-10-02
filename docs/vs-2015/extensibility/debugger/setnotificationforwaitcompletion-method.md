---
title: SetNotificationForWaitCompletion (método) | Microsoft Docs
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
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b1443bbbd49216330d1df9978052bf4d10f7157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565651"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (Método)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [SetNotificationForWaitCompletion (método)](https://docs.microsoft.com/visualstudio/extensibility/debugger/setnotificationforwaitcompletion-method).  
  
Establece o borra el bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `enabled`  
  
 `true` Para establecer el bit; `false` al anular el bit.  
  
## <a name="exceptions"></a>Excepciones  
  
## <a name="remarks"></a>Comentarios  
 El depurador establece este bit para ayudar a paso fuera de un cuerpo de método asincrónico. Si `enabled` es `true`, este método debe llamarse únicamente en una tarea que no se ha completado todavía. Si `enabled` es `false`, este método puede llamarse en las tareas completadas. En cualquier caso, solo debe usarse para tareas de la promesa de estilo.  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Vea también  
 [Clase Task](../../extensibility/debugger/task-class-internal-members.md)

