---
title: Modo de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25adcc12e6d474899165c1a486fd550f34dd99a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574846"
---
# <a name="entering-break-mode"></a>Especificación de modo de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [escribir el modo de interrupción](https://docs.microsoft.com/visualstudio/extensibility/debugger/entering-break-mode).  
  
El siguiente describe el proceso que se produce cuando se encuentra un punto de interrupción después de la ejecución paso a paso en una función, que se ejecutan en la línea de código fuente que tiene el cursor en ella o que se ejecutan en un punto de interrupción.  
  
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
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)

