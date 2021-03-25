---
title: Errores de puntos de interrupción | Microsoft Docs
description: Obtenga información sobre el proceso en el que un punto de interrupción intenta enlazarse al código, pero produce un error y cómo solucionar los errores de los puntos de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12e8efc7fc110f3f5c20c92d97cf3692094ef6aa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055248"
---
# <a name="breakpoint-errors"></a>Errores de punto de interrupción
A continuación se describe el proceso cuando un punto de interrupción intenta enlazarse al código pero se produce un error.

## <a name="troubleshoot-a-breakpoint-error"></a>Solucionar un error de punto de interrupción

1. El motor DE depuración (DE) envía un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al administrador de depuración de la sesión (SDM).

2. El SDM llama a [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) para obtener el punto de interrupción de error.

3. El SDM llama a [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obtener el punto de interrupción pendiente en el que se originó el punto de interrupción de error.

4. El SDM llama a [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obtener el motivo por el que no se pudo enlazar el punto de interrupción de error.

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
