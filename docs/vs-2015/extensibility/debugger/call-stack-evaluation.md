---
title: Evaluación de la pila de llamadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146415"
---
# <a name="call-stack-evaluation"></a>Evaluación de la pila de llamadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para ver los marcos de pila de la pila de llamadas durante el modo de interrupción, debe implementar el método [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## <a name="methods-for-evaluation"></a>Métodos de evaluación  
 Para un motor de depuración simple (DE), puede haber un solo marco de pila. Para examinar el marco de pila durante el modo de interrupción, debe implementar los métodos siguientes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto de código para un marco de pila. El contexto de código representa el puntero de instrucción actual en un marco de pila.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento para un marco de pila. El contexto del documento representa la ubicación actual en el código fuente de un marco de pila. Necesario para ver el código fuente cuando se detiene en un programa.|  
  
 Estos métodos requieren la implementación de varias interfaces y métodos relacionados con el contexto. Por lo tanto, debe implementar el método [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) y los siguientes métodos de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtiene el intervalo de instrucciones de archivo de un contexto de documento.|  
  
 Para enumerar los contextos de código, debe implementar todos los métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Consulte también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
