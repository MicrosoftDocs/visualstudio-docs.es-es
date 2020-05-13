---
title: Evaluador de Expresiones (Expresion Evaluator) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738689"
---
# <a name="expression-evaluator"></a>Evaluador de expresiones
Los evaluadores de expresiones (EE) examinan la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que permite que el usuario las vea cuando el IDE está en modo de interrupción.

## <a name="use-expression-evaluators"></a>Usar evaluadores de expresiones
 Las expresiones se crean mediante el método [ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) como se indica a continuación:

1. El motor de depuración (DE) implementa el [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.

2. El paquete de `IDebugExpressionContext2` depuración obtiene un objeto de un `IDebugStackFrame2::ParseText` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz y, a continuación, llama al método en él para obtener un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto.

3. El paquete de depuración llama al método [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o al método [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener el valor de la expresión. `IDebugExpression2::EvaluateAsync`se llama desde la ventana Comando/Inmediato. Todos los demás componentes de la interfaz de usuario llaman a `IDebugExpression2::EvaluateSync`.

4. El resultado de la evaluación de expresiones es un objeto [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) que contiene el nombre, el tipo y el valor del resultado de la evaluación de expresiones.

   Durante la evaluación de expresiones, EE requiere información del componente del proveedor de símbolos. El proveedor de símbolos proporciona la información simbólica utilizada para identificar y comprender la expresión analizada.

   Cuando se completa la evaluación de expresiones asincrónicas, la DE envía un evento asincrónico a través del administrador de depuración de sesión (SDM) para notificar al IDE que la evaluación de expresiones se ha completado. Además, el resultado de la evaluación `IDebugExpression2::EvaluateSync` se devuelve de la llamada al método.

## <a name="implementation-notes"></a>Notas de implementación
 Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración esperan hablar con el evaluador de expresiones mediante interfaces de Common Language Runtime (CLR). Como resultado, un evaluador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] expresiones que funciona con los motores de depuración debe admitir CLR (se puede encontrar una [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte de la extensión ).

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
