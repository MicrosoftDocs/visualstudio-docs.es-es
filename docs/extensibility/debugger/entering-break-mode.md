---
title: "Modo de interrupci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modo de interrupción"
  - "depurar [SDK de depuración], modo de interrupción"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Modo de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso que se produce cuando un punto de interrupción se encuentra después de entrar en una función, ejecutándose a la línea de código fuente con el cursor en él, o ejecutando un punto de interrupción.  
  
## Proceso en modo de interrupción  
  
1.  El motor de depuración \(DE\) envía [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), o cualquier otro evento que detiene para hacer el IDE para entrar en el modo de interrupción.  
  
2.  El SDM obtiene la información de la pila de llamadas del subproceso, como sigue:  
  
    -   [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2:: GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2:: Siguiente](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener la información del código fuente  
  
    -   [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) para obtener el nombre de archivo  
  
    -   [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obtener el intervalo de la instrucción  
  
    -   [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obtener la información de memoria  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)