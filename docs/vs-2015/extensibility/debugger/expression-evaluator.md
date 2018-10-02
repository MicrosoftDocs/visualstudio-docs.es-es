---
title: Evaluador de expresiones | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8856284869a256f9be08931b36db644621a3202d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576110"
---
# <a name="expression-evaluator"></a>Evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [evaluador](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluator).  
  
Evaluadores de expresión (EE) examina la sintaxis de un idioma para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que les permite ver el usuario cuando el IDE está en modo de interrupción.  
  
## <a name="using-expression-evaluators"></a>Uso de evaluadores de expresión  
 Las expresiones se crean mediante el [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método, como se indica a continuación:  
  
1.  Implementa el motor de depuración (DE) la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.  
  
2.  Obtiene el paquete de depuración un `IDebugExpressionContext2` objeto desde un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz y, a continuación, llama a la `IDebugStackFrame2::ParseText` método en él para obtener un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto.  
  
3.  El paquete de depuración llama a la [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) método o la [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método para obtener el valor de la expresión. `IDebugExpression2::EvaluateAsync` se llama desde la ventana de comando o inmediato. Llamar todos los demás componentes de interfaz de usuario `IDebugExpression2::EvaluateSync`.  
  
4.  El resultado de evaluación de la expresión es un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que contiene el nombre, tipo y valor del resultado de la evaluación de expresiones.  
  
 Durante la evaluación de expresión, el EE requiere información desde el componente de proveedor de símbolos. El proveedor de símbolos proporciona la información simbólica que se usa para identificar y entender la expresión analizada.  
  
 Una vez completada la evaluación de expresiones asincrónica, se envía un evento asincrónico por la DE a través del Administrador de depuración de la sesión (SDM) para notificar el IDE que la evaluación de expresiones ha finalizado. Una vez completada la evaluación de expresiones sincrónica, se devuelve el resultado de la evaluación de la llamada a la `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Notas de implementación  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motores de depuración que se esperan para comunicarse con el evaluador de expresiones mediante interfaces de Common Language Runtime (CLR). Como resultado, un evaluador de expresiones que funciona con el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motores de depuración deben admitir el CLR (encontrará una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte de la [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)

