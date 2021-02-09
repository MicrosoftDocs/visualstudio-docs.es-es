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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcd81b79fa43d86036a7fd1ac0ad813e6e2ebb78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894977"
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

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
