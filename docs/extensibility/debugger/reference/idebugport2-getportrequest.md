---
description: Obtiene la descripción de un puerto que se usó anteriormente para crear el puerto (si está disponible).
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 084e8bb94356ea4e2cff1fa83e83e7e08b35134e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142874"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtiene la descripción de un puerto que se usó anteriormente para crear el puerto (si está disponible).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parámetros
`ppRequest`\
enuncia Devuelve un objeto [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) que representa la solicitud que se usó para crear el puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_PORT_NO_REQUEST` si no se creó un puerto mediante una solicitud de puerto [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .

## <a name="see-also"></a>Consulte también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
