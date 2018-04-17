---
title: Alcanzar un punto de interrupción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 9f4788f8a038a274d6d94b4edf368e30ef495665
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="hitting-a-breakpoint"></a>Alcanzar un punto de interrupción
A continuación describe el proceso cuando el motor de depuración (Alemania) alcanza un punto de interrupción mientras se ejecuta o ejecución paso a paso:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solución de problemas de un punto de interrupción de llamadas  
  
1.  Los envíos DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz como un **EVENT_SYNC_STOP**.  
  
2.  El Administrador de sesión de depuración (SDM) llama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción que se alcanzó.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)