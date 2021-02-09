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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862180"
---
# <a name="deleting-a-breakpoint"></a>Eliminar un punto de interrupción
A continuación se describe el proceso al eliminar un punto de interrupción pendiente:

## <a name="deletion-process"></a>Proceso de eliminación
 El administrador de depuración de sesión (SDM) llama al método [IDebugPendingBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para quitar el punto de interrupción pendiente y todos los puntos de interrupción enlazados enlazados a él.

> [!NOTE]
> Un solo punto de interrupción enlazado también puede eliminarse mediante una llamada a [IDebugBoundBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
