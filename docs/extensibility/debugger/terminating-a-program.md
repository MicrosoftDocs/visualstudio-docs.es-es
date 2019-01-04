---
title: Terminación de un programa | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 28be8f34602a3a175c40d630463686f0ca99c919
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958857"
---
# <a name="terminating-a-program"></a>Terminación de un programa
La siguiente sección describe la terminación de un programa con un subproceso único.  
  
## <a name="termination-process"></a>Proceso de finalización  
  
1. Los envíos DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con válido [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Los envíos DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con válido [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   El IDE entra en modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama a [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa desde el puerto.  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)