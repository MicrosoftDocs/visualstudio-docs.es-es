---
title: IDebugPropertyField ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720695"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Esta interfaz proporciona las funciones que permiten obtener y establecer una propiedad.

## <a name="syntax"></a>Sintaxis

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa [el IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Esta interfaz es una especialización que admite el concepto de propiedades en una clase.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de la [interfaz IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si el método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_KIND_PROP`.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de las interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtiene el método que obtiene la propiedad.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Obtiene el método que establece la propiedad.|

## <a name="remarks"></a>Observaciones
 Una propiedad es un concepto de código administrado y representa un método que se trata como una variable. Las propiedades no existen en C++no administrado.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
