---
title: IDebugBinder ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735971"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz enlaza un campo de símbolo, normalmente devuelto por el proveedor de símbolos, a un contexto de memoria u objeto que contiene el valor actual del símbolo.

## <a name="syntax"></a>Sintaxis

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz admite la evaluación de expresiones y debe implementarse en el motor de depuración (DE).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz se utiliza en el proceso de evaluación de expresiones y normalmente se utiliza en la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugBinder`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtiene el contexto de memoria u objeto que contiene el valor actual del símbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina el tipo de tiempo de ejecución de un objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convierte una ubicación de objeto o una dirección de memoria en un contexto de memoria.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtiene el tipo exacto de una variable.|

## <a name="remarks"></a>Observaciones
 Esta interfaz devuelve objetos que utiliza el evaluador de expresiones en árboles de análisis. El evaluador de expresiones analiza una expresión mediante el proveedor de símbolos para convertir los símbolos de la expresión en instancias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que describen cada símbolo en términos de su tipo y ubicación en el código fuente. El [método](../../../extensibility/debugger/reference/idebugbinder-bind.md) Bind `IDebugField` convierte objetos en objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que conectan o enlazan un tipo de símbolo a un valor real en memoria. A `IDebugObject` continuación, estos objetos se almacenan en un árbol de análisis para su posterior evaluación.

## <a name="requirements"></a>Requisitos
 Encabezado: ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
