---
title: "Evaluaci&#243;n de la pila de llamadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depuración [SDK de depuración], la evaluación de pila de llamadas"
  - "pilas de llamadas, evaluación"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Evaluaci&#243;n de la pila de llamadas
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para ver los marcos de pila de la pila de llamadas durante el modo de interrupción, debe implementar el método de [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## métodos para la evaluación  
 Para un motor simple de depuración \(DE\), podría haber un marco de pila.  Para examinar el marco de pila durante el modo de interrupción, debe implementar los métodos siguientes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto del código para un marco de pila.  El contexto del código representa el puntero de instrucción actual en un marco de pila.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento para un marco de pila.  El contexto del documento representa la ubicación actual en el código fuente para un marco de pila.  Necesario para ver el código fuente cuando la ejecución se detenga en un programa.|  
  
 estos métodos requieren la implementación de varias interfaces y métodos contexto\-relacionados.  Por tanto, debe implementar el método de [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) y los métodos siguientes de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtiene el intervalo de la instrucción de un contexto del documento.|  
  
 Para enumerar contextos de código, debe implementar todos los métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)