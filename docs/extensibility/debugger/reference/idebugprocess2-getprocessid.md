---
title: 'IDebugProcess2:: Getprocessid (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df7b90d4096f651e0f055f9c92343df2a2712fe9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894899"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Obtiene el GUID para este proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Parámetros
`pguidProcessId`\
enuncia Devuelve el GUID para este proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 El identificador único global (GUID) identifica este proceso de todos los demás procesos que se ejecutan en el sistema.

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
