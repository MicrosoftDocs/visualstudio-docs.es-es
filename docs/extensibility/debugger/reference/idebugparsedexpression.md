---
title: IDebugParsedExpression | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b877dd974a0b96a176b54f308a6317e7324b6ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa una expresión analizada lista para ser evaluada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador de expresiones implementa esta interfaz para representar una expresión analizada que está lista para su evaluación.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente muestra el método de `IDebugParsedExpression`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Evalúa la expresión analizada.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando el llamador está listo para evaluar la expresión, se llama a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para devolver un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que contiene el resultado de la evaluación. Este enfoque de dos partes para evaluación, análisis, a continuación, evaluar, permite a la expresión analizada evaluar varias veces, omitiendo el laborioso proceso de analizar la expresión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Análisis](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)