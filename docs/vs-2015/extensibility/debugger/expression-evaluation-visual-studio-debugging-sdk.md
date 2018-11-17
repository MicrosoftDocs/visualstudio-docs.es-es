---
title: Evaluación de expresiones (SDK de depuración de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb5bfe5f5c77e7ba1881f803830e1cb3d357561b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781587"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (SDK de depuración de Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Modo de interrupción, el IDE debe poder evaluar las expresiones simples que implican varias variables del programa. Para lograr esto, el motor de depuración (DE) debe ser capaz de analizar y evaluar una expresión que se escriban en una de las ventanas del IDE.  
  
 Las expresiones se crean mediante el [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y se representan mediante resultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz.  
  
 El **IDebugExpression2** interfaz se implementa mediante las llamadas y DE su **EvalAsync** método devuelva un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz para el IDE, con el fin de mostrar el resultados de la evaluación de expresión en el IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que puede utilizarse para colocar el valor de una expresión en una ventana Inspección o en la ventana variables locales.  
  
 El administrador depuración paquete o una sesión de depuración (SDM) llama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el resultado de la evaluación. `IDebugProperty2` tiene métodos que devuelven el nombre, tipo y valor de la expresión. Esta información se muestra en distintas ventanas del depurador.  
  
## <a name="using-expression-evaluation"></a>Uso de la evaluación de expresiones  
 Para usar la evaluación de expresiones, debe implementar la [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y todos los métodos de la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, como se muestra en la tabla siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión de forma sincrónica.|  
  
 Evaluación sincrónica y asincrónica requiere la implementación de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Evaluación de expresiones asincrónico requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)

