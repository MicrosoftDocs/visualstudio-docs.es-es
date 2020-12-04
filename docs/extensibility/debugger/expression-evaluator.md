---
title: Evaluador de expresiones | Microsoft Docs
description: Obtenga información sobre los evaluadores de expresiones, que examinan la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución en modo de interrupción.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a8223e39eb804684fede50ceb2f7c859e198a272
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560140"
---
# <a name="expression-evaluator"></a>Evaluador de expresiones
Los evaluadores de expresiones (EE) examinan la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que permite que el usuario la vea cuando el IDE está en modo de interrupción.

## <a name="use-expression-evaluators"></a>Usar evaluadores de expresiones
 Las expresiones se crean mediante el método [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , como se indica a continuación:

1. El motor DE depuración (DE) implementa la interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

2. El paquete de depuración obtiene un `IDebugExpressionContext2` objeto de una interfaz [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) y, a continuación, llama al `IDebugStackFrame2::ParseText` método en él para obtener un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

3. El paquete de depuración llama al método [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o al método [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener el valor de la expresión. `IDebugExpression2::EvaluateAsync` se llama desde la ventana comando/inmediato. Todos los demás componentes de la interfaz de usuario llaman a `IDebugExpression2::EvaluateSync` .

4. El resultado de la evaluación de expresiones es un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , que contiene el nombre, el tipo y el valor del resultado de la evaluación de la expresión.

   Durante la evaluación de expresiones, el EE requiere información del componente de proveedor de símbolos. El proveedor de símbolos proporciona la información simbólica que se usa para identificar y entender la expresión analizada.

   Cuando se completa la evaluación DE expresiones asincrónicas, el DE se envía a través del administrador DE depuración DE sesión (SDM) para notificar al IDE que se ha completado la evaluación de la expresión. Y, a continuación, el resultado de la evaluación se devuelve desde la llamada al `IDebugExpression2::EvaluateSync` método.

## <a name="implementation-notes"></a>Notas de implementación
 Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración esperan comunicarse con el evaluador de expresiones mediante interfaces de Common Language Runtime (CLR). Como resultado, un evaluador de expresiones que funciona con los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración debe admitir CLR (se puede encontrar una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte del [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
