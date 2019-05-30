---
title: Errores de punto de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31eabde4ae19ae7342188a5d2a16374b9c94afc0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332554"
---
# <a name="breakpoint-errors"></a>Errores de punto de interrupción
Siguiente describe el proceso cuando un punto de interrupción intenta enlazar al código, pero se produce un error.

## <a name="troubleshoot-a-breakpoint-error"></a>Solucionar un error de punto de interrupción

1. El motor de depuración (DE) envía un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) el Administrador de depuración de la sesión (SDM).

2. Las llamadas SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) para obtener el punto de interrupción de error.

3. Las llamadas SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obtener el punto de interrupción pendiente desde la que se originó el punto de interrupción de error.

4. Las llamadas SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obtener el motivo de error para enlazar el punto de interrupción de error.

## <a name="see-also"></a>Vea también
- [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)