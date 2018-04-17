---
title: IDebugFunctionObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e7281be40e7559171c82da81d89f717bea3c8ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador de expresiones implementa esta interfaz para representar una función.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz es una especialización de la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de interfaz y se obtiene mediante [QueryInterface](/cpp/atl/queryinterface) en el `IDebugObject` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), el `IDebugFunctionObject` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crea un objeto de datos primitivo.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crea un objeto mediante un constructor.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crea un objeto con ningún constructor.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crea un objeto de matriz.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crea un objeto de cadena.|  
|[evaluar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Llama a la función y devuelve el valor resultante como un objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz permite que el evaluador de expresiones representar las funciones en un árbol de análisis. El `Create` métodos en esta interfaz se utilizan para construir objetos que representan los parámetros de entrada al método. La función, a continuación, se puede ejecutar mediante una llamada a la [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) método, que devuelve un objeto que representa el valor devuelto de la función.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)