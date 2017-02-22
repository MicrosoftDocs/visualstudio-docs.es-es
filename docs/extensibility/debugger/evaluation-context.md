---
title: "Contexto de evaluaci&#243;n | Microsoft Docs"
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
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones, contexto"
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Contexto de evaluaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando el motor de depuración \(DE\) llama el evaluador de expresiones \(EE\), se pasan tres argumentos a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinar el contexto para buscar y evaluar los símbolos, como se muestra en la tabla siguiente.  
  
## Argumentos  
  
|Argumento|Descripción|  
|---------------|-----------------|  
|`pSymbolProvider`|Un [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaz que especifica el controlador de símbolos \(SH\) que se usará para identificar el símbolo.|  
|`pAddress`|Un [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaz que especifica el punto de ejecución actual. Esto puede utilizarse para encontrar el método que contiene el código que se está ejecutando.|  
|`pBinder`|Un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaz que puede utilizar para buscar el tipo de un símbolo de acuerdo con su nombre y valor.|  
  
 `IDebugParsedExpression::EvaluateSync` Devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el valor resultante y su tipo de interfaz.  
  
## Vea también  
 [Interfaces de evaluador de expresión de clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)