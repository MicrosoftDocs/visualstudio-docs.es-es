---
description: Esta interfaz representa una posición abstracta de una función en un documento de origen.
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5afd44827d8d9b6f244bc914728bd090261ab25
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063479"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Esta interfaz representa una posición abstracta de una función en un documento de origen.

## <a name="syntax"></a>Sintaxis

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar la posición de una función dentro de un documento de origen.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz se proporciona como parte de una Unión [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (concretamente, una estructura [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) ) que, a su vez, forma parte de la estructura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , que se usa para crear un punto de interrupción pendiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugFunctionPosition2` .

|Método|Descripción|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtiene el nombre de la función a la que esta posición es relativa.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Obtiene el desplazamiento desde el principio de la función.|

## <a name="remarks"></a>Observaciones
 La posición representada por esta interfaz está basada en texto, en concreto, una estructura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
