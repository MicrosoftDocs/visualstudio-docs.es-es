---
title: Golpear un punto de interrupción | Microsoft Docs
description: En este artículo se describe el proceso que tiene lugar cuando el motor de depuración alcanza un punto de interrupción durante la ejecución o paso a paso.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560855"
---
# <a name="hit-a-breakpoint"></a>Llegar a un punto de interrupción
En la siguiente sección se describe el proceso en el que el motor DE depuración (DE) alcanza un punto de interrupción durante la ejecución o paso a paso:

## <a name="troubleshoot-a-hit-breakpoint"></a>Solucionar problemas de un punto de interrupción de acierto

1. El DE envía una interfaz [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) como **EVENT_SYNC_STOP**.

2. El administrador de depuración de sesión (SDM) llama a [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción que se alcanzó.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
