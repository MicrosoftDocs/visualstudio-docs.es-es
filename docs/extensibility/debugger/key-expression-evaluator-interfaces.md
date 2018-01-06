---
title: Interfaces del evaluador de expresiones de clave | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1e0d655f18ec7ec50dffa52e3ac4ce363fb02fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces de evaluador de expresión de clave
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Al escribir un evaluador de expresiones (EE), junto con el contexto de evaluación, debe estar familiarizado con las interfaces siguientes.  
  
## <a name="interface-descriptions"></a>Descripciones de la interfaz  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Tiene un método único, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtiene una estructura de datos que representa el punto actual de ejecución. Esta estructura de datos es uno de los tres argumentos que pasa el motor de depuración (Alemania) a la [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) método para evaluar una expresión. Esta interfaz se implementa normalmente por el proveedor de símbolos.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Tiene la [enlazar](../../extensibility/debugger/reference/idebugbinder-bind.md) método, que obtiene el área de memoria que contiene el valor actual de un símbolo. Proporciona tanto el método que lo contiene, representado por un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto y el símbolo, representado por un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto, `IDebugBinder::Bind` devuelve el valor del símbolo. `IDebugBinder`Normalmente se implementa mediante el Alemania.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Representa un tipo de datos simple. Para los tipos más complejos, como matrices y métodos, use la clase derivada [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) y [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaces, respectivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) es otra interfaz derivada importante que representa los símbolos que contiene otros símbolos, como métodos o clases. El `IDebugField` interfaz (y sus derivados) normalmente se implementan mediante el proveedor de símbolos.  
  
     Un `IDebugField` objeto puede utilizar para buscar el nombre y el tipo de un símbolo de y, junto con un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) de objetos, puede utilizar para encontrar su valor.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Representa los bits reales del valor de tiempo de ejecución de un símbolo. [Enlazar](../../extensibility/debugger/reference/idebugbinder-bind.md) toma una [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto, que representa un símbolo y devuelve un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto. El [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) método devuelve el valor del símbolo en un búfer de memoria. Normalmente, un Alemania implementa esta interfaz para representar el valor de una propiedad en la memoria.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Esta interfaz representa el evaluador de expresiones propio. El método clave es [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que devuelve un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaz.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Esta interfaz representa una expresión analizada lista para ser evaluada. El método clave es [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que devuelve un IDebugProperty2 que representa el valor y el tipo de la expresión.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Esta interfaz representa un valor y su tipo y es el resultado de evaluación de una expresión.  
  
## <a name="see-also"></a>Vea también  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)