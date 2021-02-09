---
title: 'IDebugProperty2:: GetReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 270a8cc755318578f680e4266ca01e35dee20bb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850899"
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

## <a name="parameters"></a>Parámetros
`ppRererence`\
enuncia Devuelve un objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa una referencia al valor de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error, normalmente `E_NOTIMPL` o `E_GETREFERENCE_NO_REFERENCE` .

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
