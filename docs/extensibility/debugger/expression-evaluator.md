---
title: Evaluador de expresiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dd2cc4409dbdb7650454715e133fd76dda5b780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator"></a>Evaluador de expresiones
Evaluadores de expresión (EE) examina la sintaxis de un idioma para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que les permite ver el usuario cuando el IDE está en modo de interrupción.  
  
## <a name="using-expression-evaluators"></a>Uso de evaluadores de expresión  
 Las expresiones se crean utilizando el [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método, tal como se indica a continuación:  
  
1.  El motor de depuración (Alemania) implementa la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.  
  
2.  Obtiene el paquete de depuración un `IDebugExpressionContext2` objeto desde un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz y, a continuación, llama el `IDebugStackFrame2::ParseText` método para obtener un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto.  
  
3.  Las llamadas de paquete de depuración del [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) método o la [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método para obtener el valor de la expresión. `IDebugExpression2::EvaluateAsync` se llama desde la ventana de comandos/inmediato. Llamar todos los demás componentes de interfaz de usuario `IDebugExpression2::EvaluateSync`.  
  
4.  El resultado de evaluación de la expresión es un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que contiene el nombre, el tipo y el valor del resultado de la evaluación de expresiones.  
  
 Al evaluar una expresión, el EE requiere información desde el componente de proveedor de símbolos. El proveedor de símbolos proporciona la información simbólica que se usa para identificar y describir la expresión analizada.  
  
 Una vez completada la evaluación de expresiones asincrónico, un evento asincrónico se envía por la DE mediante el Administrador de sesión de depuración (SDM) para notificar el IDE que la evaluación de expresiones ha finalizado. Una vez completada la evaluación de expresiones sincrónica, se devuelve el resultado de la evaluación de la llamada a la `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Notas de implementación  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración que se esperan para comunicarse con el evaluador de expresiones mediante interfaces de Common Language Runtime (CLR). Como resultado, un evaluador de expresiones que funciona con la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración deben ser compatible con el CLR (encontrará una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte de la [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)