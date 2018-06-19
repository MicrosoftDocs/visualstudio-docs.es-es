---
title: Contexto de evaluación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 266fe85bedeea2c7e3dae7726d113d66a4b2b1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101139"
---
# <a name="evaluation-context"></a>Contexto de evaluación
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando el motor de depuración (Alemania) llama el evaluador de expresiones (EE), se pasan tres argumentos a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinar el contexto para buscar y evaluar los símbolos, como se muestra en la tabla siguiente.  
  
## <a name="arguments"></a>Argumentos  
  
|Argumento|Descripción|  
|--------------|-----------------|  
|`pSymbolProvider`|Un [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaz que especifica el controlador de símbolos (SH) que se usará para identificar el símbolo.|  
|`pAddress`|Un [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaz que especifica el punto actual de ejecución. Esto se puede utilizar para buscar el método que contiene el código que se está ejecutando.|  
|`pBinder`|Un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaz que puede usarse para buscar el valor y el tipo de un símbolo de acuerdo con su nombre.|  
  
 `IDebugParsedExpression::EvaluateSync` Devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el valor resultante y su tipo.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluador de expresión de clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)