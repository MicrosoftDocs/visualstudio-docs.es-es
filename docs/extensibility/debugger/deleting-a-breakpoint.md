---
title: Eliminar un punto de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7551ee12993780544bbb9c9eb127a9bfb4364e8d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345826"
---
# <a name="deleting-a-breakpoint"></a>Eliminar un punto de interrupción
El siguiente describe el proceso al eliminar un punto de interrupción pendiente:

## <a name="deletion-process"></a>Proceso de eliminación
 El Administrador de depuración de la sesión (SDM) llama a la [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) método para quitar el punto de interrupción pendiente y enlazados todos los puntos de interrupción enlazado de él.

> [!NOTE]
> También se puede eliminar un punto de interrupción enlazado mediante una llamada a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Vea también
- [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)