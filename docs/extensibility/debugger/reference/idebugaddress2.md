---
description: Esta interfaz proporciona acceso al identificador del proceso que posee el objeto cuya dirección está representada por esta interfaz.
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58a3f01472f60996b7094334de8cb2dbd79acac0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143966"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Esta interfaz proporciona acceso al identificador del proceso que posee el objeto cuya dirección está representada por esta interfaz.

## <a name="syntax"></a>Syntax

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Esta interfaz proporciona acceso al identificador del proceso que posee el objeto que está relacionado con esta dirección.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de la interfaz [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Además de los métodos heredados de la interfaz [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera el identificador del proceso que posee el objeto representado por esta interfaz.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
