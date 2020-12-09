---
title: Crear un punto de interrupción | Microsoft Docs
description: Obtenga información sobre las llamadas de método que el administrador de depuración de sesión realiza cuando se carga el módulo necesario para enlazar un punto de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba192a0cda2e63453984d3de7d6007744cc401b7
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914233"
---
# <a name="create-a-breakpoint"></a>Crear un punto de interrupción
A continuación se describe el proceso de creación de un punto de interrupción.

## <a name="methods-in-breakpoint-creation"></a>Métodos en la creación de puntos de interrupción
 Cuando se carga el módulo necesario para enlazar un punto de interrupción, el administrador de depuración de sesión (SDM) llama a los métodos siguientes:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > Solo se llama a **CanBind** cuando un usuario crea un punto de interrupción desde la ventana **puntos de interrupción** .

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
