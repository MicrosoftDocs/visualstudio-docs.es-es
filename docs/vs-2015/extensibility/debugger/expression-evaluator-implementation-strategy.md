---
title: Estrategia de implementación del evaluador de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843118"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estrategia de implementación del evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Un enfoque para crear rápidamente un evaluador de expresiones (EE) es primero implementar el código mínimo necesario para mostrar las variables locales en la ventana **variables** locales. Resulta útil saber que cada línea de la ventana **variables locales** muestra el nombre, el tipo y el valor de una variable local, y que los tres se representan mediante un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . El nombre, el tipo y el valor de una variable local se pueden obtener a partir de un `IDebugProperty2` objeto llamando a su método [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Para obtener más información sobre cómo mostrar las variables locales en la ventana **variables** locales, vea [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Debate  
 Una posible secuencia de implementación comienza con la implementación de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Los métodos [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) deben implementarse para mostrar variables locales. La llamada a `IDebugExpressionEvaluator::GetMethodProperty` devuelve un `IDebugProperty2` objeto que representa un método: es decir, un objeto [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Los propios métodos no se muestran en la ventana **variables locales** .  
  
 El método [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) debe implementarse a continuación. El motor de depuración (DE) llama a este método para obtener una lista de variables locales y argumentos pasando `IDebugProperty2::EnumChildren` un `guidFilter` argumento de `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` llama a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando los resultados en una sola enumeración. Consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles.  
  
## <a name="see-also"></a>Consulte también  
 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)
