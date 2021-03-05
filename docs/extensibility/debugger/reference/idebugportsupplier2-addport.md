---
description: Agrega un puerto.
title: 'IDebugPortSupplier2:: AddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14232ac49b3862c635a41c25e79c7ab166fa24ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169241"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Agrega un puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parámetros
`pRequest`\
de Objeto [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) que describe el puerto que se va a agregar.

`ppPort`\
enuncia Devuelve un objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método crea realmente el puerto solicitado y lo agrega a la lista interna de puertos activos del proveedor del puerto. Se puede llamar primero al método [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para evitar posibles retrasos que requieran mucho tiempo.

## <a name="see-also"></a>Consulte también
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
