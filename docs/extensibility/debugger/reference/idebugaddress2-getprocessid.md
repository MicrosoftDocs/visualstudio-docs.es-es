---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d2fce11c4ddd5a2ca882749ff4ae4a9b3ee0434
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723323"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Recupera el identificador de proceso que posee el objeto representado por este [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

#### <a name="parameters"></a>Parámetros
 `pProcID`

 [out] El identificador de proceso.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)