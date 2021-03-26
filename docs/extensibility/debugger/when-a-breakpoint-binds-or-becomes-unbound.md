---
title: Cuando un punto de interrupción se enlaza o se queda sin enlazar | Microsoft Docs
description: Obtenga información sobre los puntos de interrupción no enlazados. Cuando no se puede enlazar un punto de interrupción en el momento en que se realiza una llamada, el tiempo de enlace y la hora de creación del punto de interrupción son diferentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6e1a6acdee89be293ab4a6dc72a3d4fd4336d88
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091414"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Cuando un punto de interrupción se enlaza o se queda sin enlazar
Cuando no se puede enlazar un punto de interrupción en el momento en que se realiza una llamada al método [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , el tiempo de enlace y la hora de creación del punto de interrupción son diferentes.

## <a name="methods-called"></a>Métodos denominados
 El administrador de depuración de sesión (SDM) llama a los métodos siguientes:

1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Devuelve un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2:: enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: virtualizate](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. El método [IDebugPendingBreakpoint2:: Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) y Devuelve S_OK. El DE envía un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. Métodos [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para comprobar y obtener los puntos de interrupción enlazados.

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
