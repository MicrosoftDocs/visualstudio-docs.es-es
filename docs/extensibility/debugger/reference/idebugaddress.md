---
description: Esta interfaz representa la dirección de un elemento.
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f49107e4d06fa828d059ebd9916ca254882ff0a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154969"
---
# <a name="idebugaddress"></a>IDebugAddress
Esta interfaz representa la dirección de un elemento. Lo devuelve el controlador de símbolos.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz para representar una dirección de un objeto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Muchos métodos de muchas interfaces devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera una estructura de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) que describe un objeto y su ubicación.|

## <a name="remarks"></a>Observaciones
 El proveedor de símbolos devuelve esta interfaz para representar un objeto y su ubicación dentro de un ámbito determinado (por ejemplo, función, método o clase). Esta interfaz se devuelve desde y se pasa a varios métodos del proveedor de símbolos y del evaluador de expresiones. Normalmente, el proveedor de símbolos es la única entidad que necesita interpretar el contenido de esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
