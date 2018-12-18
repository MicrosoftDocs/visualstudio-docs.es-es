---
title: Estrategia de implementación del evaluador de expresiones | Microsoft Docs
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
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 757e74a9dde1c580a6116342948edd4eb42f9ca3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737898"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estrategia de implementación del evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Un enfoque para crear rápidamente un evaluador de expresiones (EE) consiste en implementar el código mínimo necesario para mostrar las variables locales en el **variables locales** ventana. Resulta útil tener en cuenta que cada línea en el **variables locales** ventana muestra el nombre, tipo y valor de una variable local, y que las tres se representan mediante un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto. El nombre, tipo y valor de una variable local pueden obtenerse de una `IDebugProperty2` objeto mediante una llamada a su [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obtener más información sobre cómo mostrar las variables locales en el **variables locales** ventana, consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Explicación  
 Una secuencia de implementación posibles que se inicia con la implementación [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). El [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) métodos deben implementarse para mostrar las variables locales. Una llamada a `IDebugExpressionEvaluator::GetMethodProperty` devuelve un `IDebugProperty2` objeto que representa un método: es decir, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. No se muestran los propios métodos en el **variables locales** ventana.  
  
 El [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método debe implementarse a continuación. El motor de depuración (DE) llama a este método para obtener una lista de argumentos y variables locales, pasando `IDebugProperty2::EnumChildren` un `guidFilter` argumento de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` las llamadas [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinar los resultados en una sola enumeración. Consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Implementación de un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)

