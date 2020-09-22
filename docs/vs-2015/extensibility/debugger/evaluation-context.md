---
title: Contexto de evaluación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843230"
---
# <a name="evaluation-context"></a>Contexto de evaluación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando el motor DE depuración (DE) llama al evaluador de expresiones (EE), tres argumentos pasados a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinan el contexto de búsqueda y evaluación de símbolos, tal como se muestra en la tabla siguiente.  
  
## <a name="arguments"></a>Argumentos  
  
|Argumento|Descripción|  
|--------------|-----------------|  
|`pSymbolProvider`|Una interfaz [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) que especifica el controlador de símbolos (SH) que se va a usar para identificar el símbolo.|  
|`pAddress`|Una interfaz [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) que especifica el punto de ejecución actual. Se puede usar para buscar el método que contiene el código que se está ejecutando.|  
|`pBinder`|Una interfaz [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) que se puede usar para buscar el valor y el tipo de un símbolo dado su nombre.|  
  
 `IDebugParsedExpression::EvaluateSync` Devuelve una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el valor resultante y su tipo.  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces del evaluador de expresiones clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
