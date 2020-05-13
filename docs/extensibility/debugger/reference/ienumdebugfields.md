---
title: IEnumDebugFields ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716785"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Esta interfaz representa una colección de objetos que implementan el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa por el proveedor de símbolos para proporcionar conjuntos de objetos que implementan el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz. Tenga en cuenta que esto no es una enumeración COM estándar debido a la presencia de la [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) método.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) y [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Esta interfaz implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera el siguiente conjunto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos de la enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Omite un número especificado de entradas.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Restablece la enumeración a la primera entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia de la enumeración actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera el número de entradas de la enumeración.|

## <a name="remarks"></a>Observaciones

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
