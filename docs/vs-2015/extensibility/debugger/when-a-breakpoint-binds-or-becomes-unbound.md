---
title: Cuando un punto de interrupción se enlaza o se queda sin enlazar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1425edc2c8fc3fe8c38c133388f90b18b516b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162172"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Cuando un punto de interrupción se enlaza o deja de estarlo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando no se puede enlazar un punto de interrupción en el momento en que se realiza una llamada al método [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , el tiempo de enlace y la hora de creación del punto de interrupción son diferentes.  
  
## <a name="methods-called"></a>Métodos denominados  
 El administrador de depuración de sesión (SDM) llama a los métodos siguientes:  
  
1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Devuelve un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).  
  
2. [IDebugPendingBreakpoint2:: enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3. [IDebugPendingBreakpoint2:: virtualizate](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4. El método [IDebugPendingBreakpoint2:: Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) y Devuelve S_OK. El DE envía un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5. Métodos [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para comprobar y obtener los puntos de interrupción enlazados.  
  
## <a name="see-also"></a>Consulte también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
