---
description: Esta interfaz proporciona las funciones que permiten obtener y establecer una propiedad.
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 28fbdfc16733b5cce0d1442c98c624f694adbe1d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083783"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Esta interfaz proporciona las funciones que permiten obtener y establecer una propiedad.

## <a name="syntax"></a>Sintaxis

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Esta interfaz es una especialización que admite el concepto de propiedades en una clase.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de la interfaz [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si el método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_KIND_PROP` .

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de las interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtiene el método que obtiene la propiedad.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Obtiene el método que establece la propiedad.|

## <a name="remarks"></a>Observaciones
 Una propiedad es un concepto de código administrado y representa un método que se trata como una variable. Las propiedades no existen en C++ no administrado.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
