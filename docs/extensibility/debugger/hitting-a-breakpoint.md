---
title: Alcanzar un punto de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 728258dc363f906e005c654909cb86fd782824a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935637"
---
# <a name="hit-a-breakpoint"></a>Llegar a un punto de interrupción
La siguiente sección describe el proceso cuando el motor de depuración (DE) alcanza un punto de interrupción mientras se está ejecutando o la ejecución paso a paso:  
  
## <a name="troubleshoot-a-hit-breakpoint"></a>Solución de problemas de un punto de interrupción de posicionamiento  
  
1.  Los envíos DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz como un **EVENT_SYNC_STOP**.  
  
2.  El Administrador de depuración de la sesión (SDM) llama a [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción alcanzado.  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)