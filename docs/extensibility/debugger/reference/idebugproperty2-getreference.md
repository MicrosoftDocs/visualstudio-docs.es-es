---
title: IDebugProperty2::GetReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abff655b41dbc55735b7dea2934f7d396aae5f4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916614"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Devuelve una referencia al valor de la propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

#### <a name="parameters"></a>Parámetros
 `ppRererence`

 [out] Devuelve un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa una referencia al valor de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error, normalmente `E_NOTIMPL` o `E_GETREFERENCE_NO_REFERENCE`.

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)