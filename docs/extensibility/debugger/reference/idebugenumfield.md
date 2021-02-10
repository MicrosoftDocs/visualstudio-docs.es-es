---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a67c660ec8457191e688fdd430c3f7a07b5d75c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933328"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Esta interfaz representa un tipo de enumeración.

## <a name="syntax"></a>Sintaxis

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz para representar una enumeración.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Métodos en orden VTable
 Además de los métodos de las `IDebugField` interfaces y `IDebugContainerField` , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el nombre de este tipo de enumeración.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Devuelve el nombre de la constante de enumeración asociada al valor especificado.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Devuelve el valor asociado al nombre de constante de la enumeración especificado.|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Devuelve el valor asociado al nombre de constante de la enumeración especificado, pero se omite Case.|

## <a name="remarks"></a>Notas
 Es el símbolo subyacente que está enlazado realmente a una ubicación con [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Volver](../../../extensibility/debugger/reference/idebugbinder-bind.md)
