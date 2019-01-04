---
title: Estrategia de implementación del evaluador de expresiones | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: a2f324f42bf65a9805308a7e6052e411c906a42f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888678"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estrategia de implementación del evaluador de expresiones
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Un enfoque para crear rápidamente un evaluador de expresiones (EE) consiste en implementar el código mínimo necesario para mostrar las variables locales en el **variables locales** ventana. Resulta útil tener en cuenta que cada línea en el **variables locales** ventana muestra el nombre, tipo y valor de una variable local, y que las tres se representan mediante un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto. Se obtiene el nombre, tipo y valor de una variable local de un `IDebugProperty2` objeto mediante una llamada a su [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obtener más información sobre cómo mostrar las variables locales en el **variables locales** ventana, consulte [variables locales muestra](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Explicación  
 Una secuencia de implementación posibles que se inicia con la implementación [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). El [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) se deben implementar los métodos para mostrar las variables locales. Una llamada a `IDebugExpressionEvaluator::GetMethodProperty` devuelve un `IDebugProperty2` objeto que representa un método: es decir, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. No se muestran los propios métodos en el **variables locales** ventana.  
  
 El [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método debe implementarse a continuación. El motor de depuración (DE) llama a este método para obtener una lista de argumentos y variables locales, pasando `IDebugProperty2::EnumChildren` un `guidFilter` argumento de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` las llamadas [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinar los resultados en una sola enumeración. Consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Variables locales de presentación](../../extensibility/debugger/displaying-locals.md)