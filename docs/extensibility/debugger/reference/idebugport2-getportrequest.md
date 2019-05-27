---
title: IDebugPort2::GetPortRequest | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a25863ab07c4f68f0c961692981d4125c213818b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209196"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtiene la descripción de un puerto que se había utilizado previamente para crear el puerto (si está disponible).

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
[out] Devuelve un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que representa la solicitud que se usó para crear el puerto.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  Devuelve `E_PORT_NO_REQUEST` si no se creó un puerto mediante un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) solicitud del puerto.

## <a name="see-also"></a>Vea también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)