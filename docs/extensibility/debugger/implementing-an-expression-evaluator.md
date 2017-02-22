---
title: "Implementar un evaluador de expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "evaluadores de expresiones"
  - "depurar [SDK de depuración], evaluadores de expresión"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementar un evaluador de expresiones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Evaluar una expresión es una interacción compleja entre el motor de depuración \(DE\), el proveedor de símbolos \(SP\), el objeto de enlazador y el evaluador de expresiones \(EE\) propio. Estos cuatro componentes están conectados mediante interfaces que implementa un componente y consumidos por otro.  
  
 EE toma una expresión de la DE en forma de cadena y analiza o lo evalúa. EE implementa las interfaces siguientes, que se usan por el DE:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE llama al objeto de enlazador, proporcionado por la DE obtener el valor de los símbolos y objetos. EE consume las interfaces siguientes, que se implementan mediante la DE:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementa el EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md).`IDebugProperty2` proporciona el mecanismo para describir el resultado de la evaluación de una expresión, como una variable local, un tipo primitivo o un objeto en Visual Studio, que muestra la información correspondiente en el **locales**, **inspección**, o **inmediato** ventana.  
  
 El SP se proporcionado EE por la DE cuando se solicita información. El SP implementa interfaces que describen direcciones y campos, como las siguientes interfaces y sus derivados:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE consume todas estas interfaces.  
  
## En esta sección  
 [Estrategia de implementación del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define un proceso de tres pasos para la estrategia de implementación de expresión evaluador \(EE\).  
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)