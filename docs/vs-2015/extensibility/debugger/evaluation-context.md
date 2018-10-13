---
title: Contexto de evaluación | Microsoft Docs
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
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bce0ea65aa025d7250c49b5d91f8d075a9720aa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253284"
---
# <a name="evaluation-context"></a>Contexto de evaluación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando el motor de depuración (DE) llama el evaluador de expresiones (EE), se pasan tres argumentos a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinar el contexto para buscar y evaluar los símbolos, como se muestra en la tabla siguiente.  
  
## <a name="arguments"></a>Argumentos  
  
|Argumento|Descripción|  
|--------------|-----------------|  
|`pSymbolProvider`|Un [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaz que especifica el controlador de símbolos (SH) que se usará para identificar el símbolo.|  
|`pAddress`|Un [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaz que especifica el punto de ejecución actual. Esto puede usarse para buscar el método que contiene el código que se está ejecutando.|  
|`pBinder`|Un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaz que puede usarse para buscar el valor y el tipo de un símbolo dado su nombre.|  
  
 `IDebugParsedExpression::EvaluateSync` Devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el valor resultante y su tipo.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluador de expresión de clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

