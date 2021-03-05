---
description: Esta interfaz representa un objeto de matriz.
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16162cee8a02bf02b192336425101ec4bb579106
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158532"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa un objeto de matriz.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para representar una matriz.

## <a name="notes-for-callers"></a>Notas para llamadores
 La interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) puede obtener esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface) si el objeto representa una matriz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la `IDebugObject` interfaz, se implementan los métodos siguientes en la `IDebugArrayObject` interfaz.

|Método|Descripción|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtiene el recuento de elementos de la matriz.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtiene un elemento de la matriz.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtiene todos los elementos de la matriz.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtiene el rango de la matriz.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtiene las dimensiones de la matriz.|

## <a name="remarks"></a>Observaciones
 Un evaluador de expresiones utiliza esta interfaz para representar matrices en un árbol de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
