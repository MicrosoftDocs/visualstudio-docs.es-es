---
title: Modo de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f23d11fd9e246824a888ef0f83669ade876acb7d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711285"
---
# <a name="enter-break-mode"></a>Modo de interrupción
La siguiente información describe el proceso que se produce cuando se encuentra un punto de interrupción después de la ejecución paso a paso en una función, que se ejecutan en la línea de código fuente que tiene el cursor en ella o que se ejecutan en un punto de interrupción.

## <a name="break-mode-process"></a>Proceso del modo de interrupción

1.  El motor de depuración (DE) envía [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), o cualquier otro evento de detención para hacer que el IDE especificar el modo de interrupción.

2.  El SDM Obtiene la información de la pila de llamadas del subproceso, como se indica a continuación:

    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener la información de código fuente

    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obtener el nombre de archivo

    -   [Idebugdocumentcontext2:: Getstatementrange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obtener el intervalo de instrucción

    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obtener información sobre la memoria

## <a name="see-also"></a>Vea también
- [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)