---
title: Evaluador de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152743"
---
# <a name="expression-evaluator"></a>Evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los evaluadores de expresiones (EE) examinan la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que permite que el usuario la vea cuando el IDE está en modo de interrupción.  
  
## <a name="using-expression-evaluators"></a>Usar evaluadores de expresiones  
 Las expresiones se crean mediante el método [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , como se indica a continuación:  
  
1. El motor DE depuración (DE) implementa la interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2. El paquete de depuración obtiene un `IDebugExpressionContext2` objeto de una interfaz [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) y, a continuación, llama al `IDebugStackFrame2::ParseText` método en él para obtener un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3. El paquete de depuración llama al método [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o al método [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener el valor de la expresión. `IDebugExpression2::EvaluateAsync` se llama desde la ventana comando/inmediato. Todos los demás componentes de la interfaz de usuario llaman a `IDebugExpression2::EvaluateSync` .  
  
4. El resultado de la evaluación de expresiones es un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , que contiene el nombre, el tipo y el valor del resultado de la evaluación de la expresión.  
  
   Durante la evaluación de expresiones, el EE requiere información del componente de proveedor de símbolos. El proveedor de símbolos proporciona la información simbólica que se usa para identificar y entender la expresión analizada.  
  
   Cuando se completa la evaluación DE expresiones asincrónicas, el DE se envía a través del administrador DE depuración DE sesión (SDM) para notificar al IDE que se ha completado la evaluación de la expresión. Cuando se completa la evaluación de expresiones sincrónicas, el resultado de la evaluación se devuelve desde la llamada al `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Notas de implementación  
 Los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motores de depuración esperan comunicarse con el evaluador de expresiones mediante interfaces de Common Language Runtime (CLR). Como resultado, un evaluador de expresiones que funciona con los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motores de depuración debe admitir CLR (se puede encontrar una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte del [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] ).  
  
## <a name="see-also"></a>Consulte también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
