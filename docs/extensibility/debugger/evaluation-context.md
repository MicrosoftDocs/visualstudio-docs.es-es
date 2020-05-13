---
title: Contexto de evaluación ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738802"
---
# <a name="evaluation-context"></a>Contexto de evaluación
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cuando el motor de depuración (DE) llama al evaluador de expresiones (EE), tres argumentos que se pasan a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinan el contexto para buscar y evaluar símbolos, como se muestra en la tabla siguiente.

## <a name="arguments"></a>Argumentos

|Argumento|Descripción|
|--------------|-----------------|
|`pSymbolProvider`|Una [interfaz IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) que especifica el controlador de símbolos (SH) que se usará para identificar el símbolo.|
|`pAddress`|Una interfaz [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) que especifica el punto de ejecución actual. Esta interfaz busca el método que contiene el código que se está ejecutando.|
|`pBinder`|Una [interfaz IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) que busca el valor y el tipo de un símbolo con su nombre.|

 `IDebugParsedExpression::EvaluateSync`devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el valor resultante y su tipo.

## <a name="see-also"></a>Vea también
- [Interfaces del evaluador de expresiones clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Mostrando locales](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
