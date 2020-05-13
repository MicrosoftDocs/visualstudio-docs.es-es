---
title: Entrar en el modo de interrupción ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738883"
---
# <a name="enter-break-mode"></a>Entrar en modo de interrupción
La siguiente información describe el proceso que se produce cuando se encuentra un punto de interrupción después de entrar en una función, ejecutar en la línea de código fuente que tiene el cursor en él o ejecutar en un punto de interrupción.

## <a name="break-mode-process"></a>Proceso de modo de interrupción

1. El motor de depuración (DE) envía [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)o cualquier otro evento de detención para hacer que el IDE entre en modo de interrupción.

2. El SDM consigue la información de la pila de llamadas del hilo, como sigue:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener la información del código fuente

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obtener el nombre de archivo

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obtener el intervalo de instrucciones

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obtener información de memoria

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
