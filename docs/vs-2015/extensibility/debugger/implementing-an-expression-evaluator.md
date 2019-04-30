---
title: Implementación de un evaluador de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436358"
---
# <a name="implementing-an-expression-evaluator"></a>Implementación de un evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Evaluar una expresión es una interacción compleja entre el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE) en sí mismo. Estos cuatro componentes están conectados mediante las interfaces que implementa un componente y consumidas por otro.  
  
 EE toma una expresión de la DE en forma de cadena y analiza ni lo evalúa. EE implementa las interfaces siguientes, que consuman la DE:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE llama al objeto de enlazador, proporcionado por la DE obtener el valor de símbolos y objetos. EE consume las interfaces siguientes, que se implementan mediante la DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Implementa el EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` proporciona el mecanismo para describir el resultado de evaluación de una expresión, como una variable local, un tipo primitivo o un objeto en Visual Studio, que, a continuación, muestra la información correspondiente en el **variables locales**,  **Inspección**, o **inmediato** ventana.  
  
  SP asignado a la EE por la DE cuando solicita información. SP implementa las interfaces que describen direcciones y campos, como las siguientes interfaces y sus derivados:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE consume todas estas interfaces.  
  
## <a name="in-this-section"></a>En esta sección  
 [Estrategia de implementación del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define un proceso de tres pasos para la estrategia de implementación de expresión del evaluador de expresiones (EE).  
  
## <a name="see-also"></a>Vea también  
 [Escritura de un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
