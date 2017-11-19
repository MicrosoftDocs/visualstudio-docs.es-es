---
title: "Método NotifyDebuggerOfWaitCompletion | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bfd605665627bcc9269f9225acb7d2e12418ab4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion (método)
Método de marcador de posición usado como un destino de punto de interrupción por el depurador. Este método no debe ser entre líneas ni optimizada.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Comentarios  
 Todas las operaciones de combinación con una tarea deberían llamar a este método si su bit de notificación de depurador está establecido.  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)