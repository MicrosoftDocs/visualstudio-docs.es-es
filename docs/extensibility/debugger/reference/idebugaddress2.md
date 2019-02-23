---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10af641162fe9d254eaa3c0c2f5efbf841dc154e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677648"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Esta interfaz proporciona acceso al identificador de proceso que posee el objeto cuya dirección está representado por esta interfaz.

## <a name="syntax"></a>Sintaxis

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz. Esta interfaz proporciona acceso al identificador de proceso que posee el objeto que está relacionado con esta dirección.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde el [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de vtable
 Además de los métodos heredados de la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz, esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera el identificador de proceso que posee el objeto representado por esta interfaz.|

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)