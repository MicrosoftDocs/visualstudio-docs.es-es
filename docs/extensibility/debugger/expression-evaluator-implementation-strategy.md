---
title: Estrategia de implementación del evaluador de expresiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-implementation-strategy"></a>Estrategia de implementación del evaluador de expresiones
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Un enfoque para crear rápidamente un evaluador de expresiones (EE) consiste en implementar primero el código mínimo necesario para mostrar las variables locales en el **locales** ventana. Resulta útil tener en cuenta que cada línea en el **locales** ventana muestra el nombre, el tipo y el valor de una variable local y que las tres se representan mediante un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto. El nombre, el tipo y el valor de una variable local pueden obtenerse de una `IDebugProperty2` objeto mediante una llamada a su [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obtener más información sobre cómo mostrar las variables locales en el **locales** ventana, consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Explicación  
 Una secuencia de implementación posibles que se inicia con la implementación de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). El [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) métodos deben implementarse para mostrar variables locales. Al llamar a `IDebugExpressionEvaluator::GetMethodProperty` devuelve un `IDebugProperty2` objeto que representa un método: es decir, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. Métodos no se muestran en la **locales** ventana.  
  
 El [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método debe implementarse a continuación. El motor de depuración (Alemania) llama a este método para obtener una lista de las variables locales y argumentos pasando `IDebugProperty2::EnumChildren` una `guidFilter` argumento de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` llamadas [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando los resultados de una enumeración único. Vea [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)