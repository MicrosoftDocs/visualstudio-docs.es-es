---
title: Entrando en modo de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182254"
---
# <a name="entering-break-mode"></a>Especificación de modo de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación se describe el proceso que se produce cuando se encuentra un punto de interrupción después de ejecutar paso a paso una función, ejecutar hasta la línea de código fuente que tiene el cursor o ejecutar hasta un punto de interrupción.  
  
## <a name="break-mode-process"></a>Proceso de modo de interrupción  
  
1. El motor DE depuración (DE) envía [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)o cualquier otro evento de detención para hacer que el IDE entre en modo de interrupción.  
  
2. El SDM obtiene la información de la pila de llamadas del subproceso, como se indica a continuación:  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener la información del código fuente  
  
    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obtener el nombre de archivo  
  
    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obtener el intervalo de instrucciones  
  
    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obtener información de memoria  
  
## <a name="see-also"></a>Consulte también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
