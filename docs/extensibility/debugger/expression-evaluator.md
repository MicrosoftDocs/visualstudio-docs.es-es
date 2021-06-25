---
title: Evaluador de expresiones | Microsoft Docs
description: Obtenga información sobre los evaluadores de expresiones, que examinan la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución en modo de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 998f361d8008257cb8f4a888b4d4fbb985c9c977
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900985"
---
# <a name="expression-evaluator"></a>Evaluador de expresiones
Los evaluadores de expresiones (EE) examinan la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que permite que el usuario los vea cuando el IDE está en modo de interrupción.

## <a name="use-expression-evaluators"></a>Uso de evaluadores de expresiones
 Las expresiones se crean mediante [el método ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) como se muestra a continuación:

1. El motor de depuración (DE) implementa la [interfaz IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. El paquete de depuración obtiene un objeto de una `IDebugExpressionContext2` [interfaz IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) y, a continuación, llama al método en él `IDebugStackFrame2::ParseText` para obtener un objeto [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. El paquete de depuración llama [al método EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [al método EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener el valor de la expresión. `IDebugExpression2::EvaluateAsync` se llama desde la ventana Comando/Inmediato. Todos los demás componentes de la interfaz de usuario llaman a `IDebugExpression2::EvaluateSync` .

4. El resultado de la evaluación de expresiones es un objeto [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) que contiene el nombre, el tipo y el valor del resultado de la evaluación de expresión.

   Durante la evaluación de expresiones, ee requiere información del componente del proveedor de símbolos. El proveedor de símbolos proporciona la información simbólica utilizada para identificar y comprender la expresión analizada.

   Cuando se completa la evaluación de expresiones asincrónicas, el DE envía un evento asincrónico a través del administrador de depuración de sesión (SDM) para notificar al IDE que la evaluación de expresiones se ha completado. Y, a continuación, el resultado de la evaluación se devuelve de la llamada al `IDebugExpression2::EvaluateSync` método .

## <a name="implementation-notes"></a>Notas de implementación
 Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración esperan hablar con el evaluador de expresiones mediante interfaces de Common Language Runtime (CLR). Como resultado, un evaluador de expresiones que funciona con los motores de depuración debe admitir CLR (se puede encontrar una lista completa de todas las interfaces de depuración clr en debugref.doc, que forma parte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Consulta también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
