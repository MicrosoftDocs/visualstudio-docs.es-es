---
title: La clave de las Interfaces de evaluador de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1b45b3876872ec181d2243b810b15ab860672a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089242"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces de evaluador de expresiones de clave
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Al escribir un evaluador de expresiones (EE), junto con el contexto de evaluación, debe estar familiarizado con las interfaces siguientes.  
  
## <a name="interface-descriptions"></a>Descripciones de interfaz  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Tiene un único método, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtiene una estructura de datos que representa el punto de ejecución actual. Esta estructura de datos es uno de los tres argumentos que pasa el motor de depuración (DE) a la [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) método para evaluar una expresión. Esta interfaz se implementa normalmente por el proveedor de símbolos.  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Tiene la [enlazar](../../extensibility/debugger/reference/idebugbinder-bind.md) método, que obtiene el área de memoria que contiene el valor actual de un símbolo. Proporciona tanto el método que lo contiene, representado por un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto y el símbolo, representado por un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto, `IDebugBinder::Bind` devuelve el valor del símbolo. `IDebugBinder` Normalmente se implementa por la DE.  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Representa un tipo de datos simple. Para los tipos más complejos, como matrices y métodos, use la clase derivada [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) y [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaces, respectivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) es otra interfaz derivada importante que representa los símbolos que contiene otros símbolos, como métodos o clases. El `IDebugField` interfaz (y sus derivados) normalmente se implementan mediante el proveedor de símbolos.  
  
     Un `IDebugField` objeto se puede utilizar para buscar el nombre y tipo de un símbolo de y, junto con un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) de objetos, se puede usar para encontrar su valor.  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Representa los bits reales del valor de tiempo de ejecución de un símbolo. [Enlazar](../../extensibility/debugger/reference/idebugbinder-bind.md) toma un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) object, que representa un símbolo y devuelve un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto. El [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) método devuelve el valor del símbolo en un búfer de memoria. A DE normalmente implementa esta interfaz para representar el valor de una propiedad en la memoria.  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Esta interfaz representa el evaluador de expresiones de sí mismo. El método clave es [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que devuelve un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaz.  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Esta interfaz representa una expresión analizada lista para ser evaluada. El método clave es [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que devuelve un IDebugProperty2 que representa el valor y tipo de la expresión.  
  
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Esta interfaz representa un valor y su tipo y es el resultado de evaluación de una expresión.  
  
## <a name="see-also"></a>Vea también  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)
