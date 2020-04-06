---
title: IDebugPort2::GetPortRequest ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48d39ea10e8425d5449444514489ac4b73c0a3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725332"
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
[fuera] Devuelve un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que representa la solicitud que se usó para crear el puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_PORT_NO_REQUEST` si no se creó un puerto mediante una solicitud de puerto [IDebugPortRequest2.](../../../extensibility/debugger/reference/idebugportrequest2.md)

## <a name="see-also"></a>Vea también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
