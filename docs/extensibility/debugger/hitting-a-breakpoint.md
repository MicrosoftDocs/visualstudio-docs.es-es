---
title: Golpear un punto de interrupción ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738567"
---
# <a name="hit-a-breakpoint"></a>Llegar a un punto de interrupción
La siguiente sección describe el proceso cuando el motor de depuración (DE) alcanza un punto de interrupción mientras se ejecuta o se pasa por pasos:

## <a name="troubleshoot-a-hit-breakpoint"></a>Solucionar problemas de punto de interrupción de hit

1. La DE envía un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz como un **EVENT_SYNC_STOP**.

2. El Administrador de depuración de sesión (SDM) llama a [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción que se alcanzó.

## <a name="see-also"></a>Vea también
- [Eventos del depurador de llamadas](../../extensibility/debugger/calling-debugger-events.md)
