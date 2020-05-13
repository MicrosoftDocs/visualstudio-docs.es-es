---
title: IEnumDebugAddresses ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717587"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Esta interfaz representa una colección de objetos que implementan el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa por el proveedor de símbolos para proporcionar conjuntos de objetos que implementan el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz. Tenga en cuenta que esto no es una enumeración COM estándar debido a la presencia de la [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) método.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) y [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Esta interfaz implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera el siguiente conjunto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objetos de la enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Omite un número especificado de entradas.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Restablece la enumeración a la primera entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera una copia de la enumeración actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera el número de entradas de la enumeración.|

## <a name="remarks"></a>Observaciones
 Esta interfaz se utiliza normalmente por el motor de depuración para ayudar a determinar la dirección adecuada para dar al evaluador de expresiones.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
