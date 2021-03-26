---
description: Esta interfaz representa un tipo de puntero.
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 568e442f5294b3aaa4cd8c99d7bbd1f769581ca6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087748"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Esta interfaz representa un tipo de puntero.

## <a name="syntax"></a>Sintaxis

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El proveedor de símbolos implementa esta interfaz para representar un puntero.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Además de los métodos de las `IDebugField` interfaces y `IDebugContainerField` , esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el destino del puntero.|

## <a name="remarks"></a>Observaciones
 En C/C++, un puntero puede ser un contenedor si se utiliza con la notación de matriz. Por ejemplo, dado `char *pString` , `pString` tiene un tipo de puntero a `char` . `pString[3]` tiene el tipo de un contenedor que es un puntero a `char` que hace referencia al cuarto elemento de ese contenedor.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
