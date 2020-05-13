---
title: Eliminación de un punto de interrupción ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738941"
---
# <a name="deleting-a-breakpoint"></a>Eliminación de un punto de interrupción
A continuación se describe el proceso al eliminar un punto de interrupción pendiente:

## <a name="deletion-process"></a>Proceso de eliminación
 El Administrador de depuración de sesión (SDM) llama a la [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para quitar el punto de interrupción pendiente y todos los puntos de interrupción enlazados de él.

> [!NOTE]
> Un único punto de interrupción enlazado también se puede eliminar mediante una llamada a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Vea también
- [Eventos del depurador de llamadas](../../extensibility/debugger/calling-debugger-events.md)
