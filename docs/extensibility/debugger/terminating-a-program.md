---
title: Finalizar un programa | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc5d711783b3238c9cfe42ba3fc4edd776bcb060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="terminating-a-program"></a>Finalizar un programa
La siguiente es una descripción de la finalización de un único programa de uno de esos subprocesos.  
  
## <a name="termination-process"></a>Proceso de finalización  
  
1.  Los envíos DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con válido [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Los envíos DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con válido [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 El IDE entra en modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa desde el puerto.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)