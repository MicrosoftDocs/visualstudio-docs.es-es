---
description: Representa una función y mejora la interfaz IDebugFunctionObject.
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 012cd3dd0068fe69aae8898a408435340c6b22ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072850"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Representa una función y mejora la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="syntax"></a>Sintaxis

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un evaluador de expresiones (EE) implementa esta interfaz para representar una función.

## <a name="notes-for-callers"></a>Notas para llamadores
 Los métodos de esta interfaz aplazan los de **IDebugFunctionObject** de las siguientes maneras:

- El método **IDebugEvaluate** toma marcas.

- El método **CreateObject** toma marcas y un tiempo de espera.

- El método **CreateStringObjectWithLength** toma una longitud.

## <a name="methods"></a>Métodos
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[DataSpace](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crea un objeto que usa un constructor con valores de marca de evaluación determinados y un valor de tiempo de espera.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crea un objeto de cadena que tiene la longitud especificada.|
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Llama a la función y devuelve el valor resultante como un objeto.|

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
