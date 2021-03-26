---
description: Esta interfaz representa un objeto de puntero.
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af6b8f6022a9363eb5391d6f0519603fa48668c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087605"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa un objeto de puntero.

## <a name="syntax"></a>Sintaxis

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para representar un objeto de puntero.

## <a name="notes-for-callers"></a>Notas para llamadores
 La interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) puede obtener esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface) si `IDebugObject` representa un puntero.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), la `IDebugPointerObject` interfaz expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtiene el objeto al que apunta la interfaz.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtiene el valor al que apunta la interfaz como una serie de bytes consecutivos.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Establece el valor al que apunta la interfaz a partir de una serie de bytes consecutivos.|

## <a name="remarks"></a>Observaciones
 Un evaluador de expresiones utiliza esta interfaz para representar un puntero en un árbol de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
