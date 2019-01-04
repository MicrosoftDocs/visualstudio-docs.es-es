---
title: Llame a la evaluación de la pila | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4d17c48f98a1f9bb0632df76ff5b04b0bdf5403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851227"
---
# <a name="call-stack-evaluation"></a>Evaluación de la pila de llamadas
Para ver los marcos de pila de la pila de llamadas durante el modo de interrupción, debe implementar la [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) método.  
  
## <a name="methods-for-evaluation"></a>Métodos para la evaluación  
 Para un motor de depuración simples (DE), puede haber solo un marco de pila. Para examinar el marco de pila durante el modo de interrupción, debe implementar los métodos siguientes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto de código para un marco de pila. El contexto de código representa el puntero de instrucción actual en un marco de pila.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento para un marco de pila. El contexto del documento representa la ubicación actual en el código fuente para un marco de pila. Se requiere para ver el código fuente cuando se haya detenido en un programa.|  
  
 Estos métodos requieren la implementación de varios métodos y las interfaces relacionadas con el contexto. Por lo tanto, debe implementar la [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) método y los métodos siguientes de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtiene el intervalo de la instrucción de archivo de un contexto de documento.|  
  
 Para enumerar los contextos de código, debe implementar todos los métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Vea también  
 [Evaluación de control y el estado de ejecución](../../extensibility/debugger/execution-control-and-state-evaluation.md)