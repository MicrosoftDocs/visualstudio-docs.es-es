---
description: Esta interfaz enlaza un campo de símbolo, normalmente devuelto por el proveedor de símbolos, a un contexto de memoria u objeto que contiene el valor actual del símbolo.
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4fdfe0cffce209880d870cde7b70cc1e02252413
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089087"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz enlaza un campo de símbolo, normalmente devuelto por el proveedor de símbolos, a un contexto de memoria u objeto que contiene el valor actual del símbolo.

## <a name="syntax"></a>Sintaxis

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz admite la evaluación de expresiones y debe ser implementada por el motor DE depuración (DE).

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz se usa en el proceso de evaluación de expresiones y se usa normalmente en la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugBinder` .

|Método|Descripción|
|------------|-----------------|
|[Volver](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtiene el contexto de memoria u objeto que contiene el valor actual del símbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina el tipo en tiempo de ejecución de un objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convierte una ubicación de objeto o una dirección de memoria en un contexto de memoria.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtiene un objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que se usa para crear parámetros de función.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtiene el tipo exacto de una variable.|

## <a name="remarks"></a>Observaciones
 Esta interfaz devuelve objetos utilizados por el evaluador de expresiones en los árboles de análisis. El evaluador de expresiones analiza una expresión utilizando el proveedor de símbolos para convertir los símbolos de la expresión en instancias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que describen cada símbolo en función de su tipo y ubicación en el código fuente. El método [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md) convierte `IDebugField` objetos en objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que conectan o enlazan un tipo de símbolo con un valor real de la memoria. Estos `IDebugObject` objetos se almacenan en un árbol de análisis para su posterior evaluación.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
