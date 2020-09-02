---
title: Método NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0548e1e791c41d806ccc222176ee571b037389
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153727"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion (Método)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Método de marcador de posición utilizado como destino de punto de interrupción por el depurador. Este método no debe estar alineado ni optimizado.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Comentarios  
 Todas las operaciones de combinación con una tarea deben llamar a este método si se establece el bit de notificación del depurador.  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Consulte también  
 [Task (clase)](../../extensibility/debugger/task-class-internal-members.md)
