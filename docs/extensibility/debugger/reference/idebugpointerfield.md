---
title: IDebugPointerField ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725592"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Esta interfaz representa un tipo de puntero.

## <a name="syntax"></a>Sintaxis

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El proveedor de símbolos implementa esta interfaz para representar un puntero.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde la `FIELD_TYPE_POINTER`interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve .

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Además de los `IDebugField` `IDebugContainerField` métodos en las interfaces y, esta interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el destino del puntero.|

## <a name="remarks"></a>Observaciones
 En C/C++, un puntero puede ser un contenedor si se utiliza con notación de matriz. Por ejemplo, `char *pString` `pString` dado , tiene `char`un tipo de puntero a . `pString[3]`tiene el tipo de un contenedor `char` que es un puntero a que hace referencia al cuarto elemento de ese contenedor.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
