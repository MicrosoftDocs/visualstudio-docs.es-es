---
title: IDebugExpression2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2"></a>IDebugExpression2
Esta interfaz representa una lista de expresión analizada de enlace y de evaluación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar una expresión analizada lista para ser evaluada.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) devuelve esta interfaz. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) devuelve el [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz. Estas interfaces son accesibles solo cuando se ha detenido el programa que se está depurando y un marco de pila está disponible.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugExpression2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa esta expresión de forma asincrónica.|  
|[Anulación](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónica.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa esta expresión de forma sincrónica.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando un programa se ha detenido, el Administrador de sesión de depuración (SDM) Obtiene un marco de pila de la DE con una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). El SDM, a continuación, llama [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener la [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz. Esto es seguido por una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para crear el `IDebugExpression2` interfaz que representa la expresión analizada lista para ser evaluada.  
  
 El SDM llama cualquiera [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) realmente evaluar la expresión y generar un valor.  
  
 En una implementación de `IDebugExpressionContext2::ParseText`, la DE usa de COM `CoCreateInstance` función para crear una instancia de un evaluador de expresiones y obtener un [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaz (vea el ejemplo de la `IDebugExpressionEvaluator` interfaz). A continuación, llama a la DE [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interfaz. Esta interfaz se utiliza en la implementación de `IDebugExpression2::EvaluateSync` y `IDebugExpression2::EvaluateAsync` para realizar la evaluación.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)