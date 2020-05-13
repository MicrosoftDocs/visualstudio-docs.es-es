---
title: IDebugPointerObject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725489"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa un objeto de puntero.

## <a name="syntax"></a>Sintaxis

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para representar un objeto de puntero.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz puede obtener esta `IDebugObject` interfaz mediante [QueryInterface](/cpp/atl/queryinterface) si representa un puntero.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), la `IDebugPointerObject` interfaz expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtiene el objeto al que apunta la interfaz.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtiene el valor al que apunta la interfaz como una serie de bytes consecutivos.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Establece el valor al que la interfaz apunta a una serie de bytes consecutivos.|

## <a name="remarks"></a>Observaciones
 Un evaluador de expresiones utiliza esta interfaz para representar un puntero en un árbol de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
