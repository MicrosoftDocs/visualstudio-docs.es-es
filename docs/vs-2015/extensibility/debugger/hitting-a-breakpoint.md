---
title: Golpear un punto de interrupción | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152686"
---
# <a name="hitting-a-breakpoint"></a>Llegada a un punto de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación se describe el proceso en el que el motor DE depuración (DE) alcanza un punto de interrupción durante la ejecución o paso a paso:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solucionar problemas de un punto de interrupción de acierto  
  
1. El DE envía una interfaz [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) como **EVENT_SYNC_STOP**.  
  
2. El administrador de depuración de sesión (SDM) llama a [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción que se alcanzó.  
  
## <a name="see-also"></a>Consulte también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
