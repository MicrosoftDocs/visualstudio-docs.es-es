---
title: Alcanzar un punto de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074425"
---
# <a name="hitting-a-breakpoint"></a>Llegada a un punto de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El siguiente describe el proceso cuando el motor de depuración (DE) alcanza un punto de interrupción mientras se está ejecutando o la ejecución paso a paso:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solución de problemas de un punto de interrupción de posicionamiento  
  
1. Los envíos DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz como un **EVENT_SYNC_STOP**.  
  
2. El Administrador de depuración de la sesión (SDM) llama a [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción alcanzado.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
