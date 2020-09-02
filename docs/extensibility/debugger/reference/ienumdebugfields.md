---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716785"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Esta interfaz representa una colección de objetos que implementan la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Sintaxis

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El proveedor de símbolos implementa esta interfaz para proporcionar conjuntos de objetos que implementan la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Tenga en cuenta que esto no es una enumeración COM estándar debido a la presencia del método [getCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) y [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Esta interfaz implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera el siguiente conjunto de objetos [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de la enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Omite un número especificado de entradas.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Restablece la enumeración a la primera entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia de la enumeración actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera el número de entradas de la enumeración.|

## <a name="remarks"></a>Observaciones

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
