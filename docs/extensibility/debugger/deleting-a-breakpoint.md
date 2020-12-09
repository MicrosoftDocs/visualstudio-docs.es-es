---
title: Eliminar un punto de interrupción | Microsoft Docs
description: Obtenga información sobre cómo el administrador de depuración de sesión quita un punto de interrupción pendiente y todos los puntos de interrupción enlazados que se enlazan a él cuando se elimina un punto de interrupción pendiente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915562"
---
# <a name="deleting-a-breakpoint"></a>Eliminar un punto de interrupción
A continuación se describe el proceso al eliminar un punto de interrupción pendiente:

## <a name="deletion-process"></a>Proceso de eliminación
 El administrador de depuración de sesión (SDM) llama al método [IDebugPendingBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para quitar el punto de interrupción pendiente y todos los puntos de interrupción enlazados enlazados a él.

> [!NOTE]
> Un solo punto de interrupción enlazado también puede eliminarse mediante una llamada a [IDebugBoundBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
