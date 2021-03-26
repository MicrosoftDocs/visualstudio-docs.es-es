---
description: Esta interfaz representa una función.
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0fabd43fe6f7d8ee8e5cddc6cc655088bf4a9abf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063557"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa una función.

## <a name="syntax"></a>Sintaxis

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un evaluador de expresiones implementa esta interfaz para representar una función.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz es una especialización de la interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) y se obtiene mediante [QueryInterface](/cpp/atl/queryinterface) en la `IDebugObject` interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), la `IDebugFunctionObject` interfaz expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crea un objeto de datos primitivo.|
|[DataSpace](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crea un objeto utilizando un constructor.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crea un objeto sin constructor.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crea un objeto de matriz.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crea un objeto de cadena.|
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Llama a la función y devuelve el valor resultante como un objeto.|

## <a name="remarks"></a>Observaciones
 Esta interfaz permite al evaluador de expresiones representar funciones en un árbol de análisis. Los `Create` métodos de esta interfaz se usan para construir objetos que representan los parámetros de entrada para el método. La función se puede ejecutar después llamando al método [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) , que devuelve un objeto que representa el valor devuelto de la función.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
