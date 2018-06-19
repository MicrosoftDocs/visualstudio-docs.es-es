---
title: La evaluación de expresiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102797"
---
# <a name="evaluating-expressions"></a>La evaluación de expresiones
Se crean expresiones de cadenas que se pasan desde el automático, inspección, inspección rápida o la ventana Inmediato. Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana del IDE correspondiente.  
  
## <a name="implementation"></a>Implementación  
 Las expresiones se evalúan cuando un programa se ha detenido en un punto de interrupción. La propia expresión, se representa mediante un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, que representa una expresión analizada que está lista para el enlace y evaluación dentro del contexto de evaluación de la expresión dada. El marco de pila determina el contexto de evaluación de expresión, que proporciona el motor de depuración (Alemania) mediante la implementación de la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.  
  
 Proporciona una cadena de usuario y una [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz, un motor de depuración (Alemania) puede obtener un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, pase la cadena de usuario para el [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. La interfaz de IDebugExpression2 devuelta contiene la expresión analizada lista para su evaluación.  
  
 Con el `IDebugExpression2` interfaz, el Alemania puede obtener el valor de la expresión a través de la evaluación de expresiones sincrónico o asincrónico, con [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Este valor, junto con el nombre y tipo de la variable o argumento, se envía el IDE para su presentación. El valor, el nombre y el tipo se representan mediante un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz.  
  
 Para habilitar la evaluación de expresiones, debe implementar un Alemania la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Evaluación sincrónica y asincrónica requiere la implementación de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.  
  
## <a name="see-also"></a>Vea también  
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Contexto de evaluación de expresión](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)