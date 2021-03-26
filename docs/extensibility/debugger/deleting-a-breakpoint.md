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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1d8e0d68f32ece7760805c05fd281b0e62a70003
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097284"
---
# <a name="deleting-a-breakpoint"></a>Eliminar un punto de interrupción
A continuación se describe el proceso al eliminar un punto de interrupción pendiente:

## <a name="deletion-process"></a>Proceso de eliminación
 El administrador de depuración de sesión (SDM) llama al método [IDebugPendingBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para quitar el punto de interrupción pendiente y todos los puntos de interrupción enlazados enlazados a él.

> [!NOTE]
> Un solo punto de interrupción enlazado también puede eliminarse mediante una llamada a [IDebugBoundBreakpoint2::D iminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
