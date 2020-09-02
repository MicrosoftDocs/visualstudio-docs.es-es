---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec8b26f422ca39b771a47f8eb60ee862d7d388f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568374"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa una expresión analizada lista para enlazar y evaluar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor DE depuración (DE) implementa esta interfaz para representar una expresión analizada lista para su evaluación.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) devuelve esta interfaz. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) devuelve la interfaz [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Solo se puede tener acceso a estas interfaces cuando el programa que se está depurando está en pausa y hay un marco de pila disponible.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugExpression2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa esta expresión de forma asincrónica.|  
|[Anulación](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa esta expresión sincrónicamente.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se ha detenido un programa, el administrador de depuración de la sesión (SDM) obtiene un marco de pila de de con una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Después, el SDM llama a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener la interfaz [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . A esto le sigue una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para crear la `IDebugExpression2` interfaz, que representa la expresión analizada lista para evaluarse.  
  
 El SDM llama a [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar realmente la expresión y generar un valor.  
  
 En una implementación de `IDebugExpressionContext2::ParseText` , el de utiliza la función de com `CoCreateInstance` para crear instancias de un evaluador de expresiones y obtener una interfaz [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (vea el ejemplo de la `IDebugExpressionEvaluator` interfaz). A continuación, el DE llama a [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener una interfaz [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Esta interfaz se utiliza en la implementación de `IDebugExpression2::EvaluateSync` y `IDebugExpression2::EvaluateAsync` para realizar la evaluación.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
