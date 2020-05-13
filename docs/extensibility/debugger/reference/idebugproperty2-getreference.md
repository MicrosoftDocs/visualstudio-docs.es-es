---
title: IDebugProperty2::GetReference ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f119a00139e2af44f771fa0903c73b8003dd77f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721359"
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
[fuera] Devuelve un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa una referencia al valor de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve `E_NOTIMPL` un `E_GETREFERENCE_NO_REFERENCE`código de error, normalmente o .

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
