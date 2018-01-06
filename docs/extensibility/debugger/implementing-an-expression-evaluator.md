---
title: Implementar un evaluador de expresiones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f18e2e131b6baa325bd7e0b65babee4c3679ed8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-an-expression-evaluator"></a>Implementar un evaluador de expresiones
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Evaluar una expresión es una interacción compleja entre el motor de depuración (Alemania), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE) propio. Estos cuatro componentes se conectan mediante interfaces que se implementan mediante un componente y consumidos por otro.  
  
 El EE toma una expresión de la DE en forma de cadena y analiza o evalúa. El EE implementa las interfaces siguientes, que son consumidas por la DE:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 El EE llama al objeto de enlazador, proporcionado por el Alemania, para obtener el valor de símbolos y objetos. El EE consume las interfaces siguientes, que se implementan mediante la DE:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementa el EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`proporciona el mecanismo para describir el resultado de la evaluación de una expresión, como una variable local, un tipo primitivo o un objeto, Visual Studio, que, a continuación, muestra la información correspondiente en el **locales**,  **Inspección**, o **inmediato** ventana.  
  
 El SP se otorga a lo EE si la DE cuando solicita información. El SP implementa interfaces que se describen los campos, como las siguientes interfaces y sus derivados y direcciones:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 El EE consume todas estas interfaces.  
  
## <a name="in-this-section"></a>En esta sección  
 [Estrategia de implementación del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define un proceso de tres pasos de la estrategia de implementación de expresión evaluador (EE).  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)