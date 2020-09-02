---
title: Evaluar expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151626"
---
# <a name="evaluating-expressions"></a>Evaluación de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Las expresiones se crean a partir de las cadenas que se pasan de las ventanas automático, inspección, inspección rápida o inmediata. Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana del IDE correspondiente.  
  
## <a name="implementation"></a>Implementación  
 Las expresiones se evalúan cuando un programa se detiene en un punto de interrupción. La propia expresión se representa mediante una interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , que representa una expresión analizada que está lista para el enlace y la evaluación dentro del contexto de evaluación de expresión determinado. El marco de pila determina el contexto de evaluación de expresiones, que el motor DE depuración (DE) proporciona mediante la implementación de la interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Dada una cadena de usuario y una interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motor de depuración (de) puede obtener una interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) pasando la cadena de usuario al método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . La interfaz IDebugExpression2 devuelta contiene la expresión analizada lista para su evaluación.  
  
 Con la `IDebugExpression2` interfaz, el de puede obtener el valor de la expresión a través de la evaluación de expresiones sincrónicas o asincrónicas mediante [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Este valor, junto con el nombre y el tipo de la variable o argumento, se envía al IDE para su presentación. El valor, el nombre y el tipo se representan mediante una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 Para habilitar la evaluación DE expresiones, un DE debe implementar las interfaces [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . La evaluación sincrónica y asincrónica requiere la implementación del método [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## <a name="see-also"></a>Consulte también  
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
