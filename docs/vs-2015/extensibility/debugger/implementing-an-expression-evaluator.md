---
title: Implementar un evaluador de expresiones | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842506"
---
# <a name="implementing-an-expression-evaluator"></a>Implementación de un evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 La evaluación de una expresión es una interacción compleja entre el motor DE depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el propio evaluador de expresiones (EE). Estos cuatro componentes están conectados mediante interfaces implementadas por un componente y consumidos por otro.  
  
 El EE toma una expresión de de la forma de una cadena y la analiza o la evalúa. El EE implementa las siguientes interfaces, que son utilizadas por el DE:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  El EE llama al objeto Binder, proporcionado por DE, para obtener el valor de Symbols y Objects. EE usa las siguientes interfaces, que son implementadas por el DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  El EE implementa [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` proporciona el mecanismo para describir el resultado de una evaluación de expresión, como una variable local, un tipo primitivo o un objeto, en Visual Studio, que a continuación muestra la información adecuada en las ventanas **variables locales**, **inspección**o **inmediato** .  
  
  El SP se asigna al de EE por el DE cuando solicita información. El SP implementa interfaces que describen direcciones y campos, como las siguientes interfaces y sus derivados:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE usa todas estas interfaces.  
  
## <a name="in-this-section"></a>En esta sección  
 [Estrategia de implementación del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define un proceso de tres pasos para la estrategia de implementación del evaluador de expresiones (EE).  
  
## <a name="see-also"></a>Consulte también  
 [Escritura de un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
