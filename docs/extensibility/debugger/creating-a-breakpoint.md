---
title: Creación de un punto de interrupción ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d252f1310c3e251c44525cd94c4d9a2943d8171d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739044"
---
# <a name="create-a-breakpoint"></a>Crear un punto de interrupción
A continuación se describe el proceso de creación de un punto de interrupción.

## <a name="methods-in-breakpoint-creation"></a>Métodos en la creación de puntos de interrupción
 Cuando se carga el módulo necesario para enlazar un punto de interrupción, el administrador de depuración de sesión (SDM) llama a los métodos siguientes:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** se llama sólo cuando un usuario hace un punto de interrupción desde el **punto** de interrupción ventana.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Vea también
- [Eventos del depurador de llamadas](../../extensibility/debugger/calling-debugger-events.md)
