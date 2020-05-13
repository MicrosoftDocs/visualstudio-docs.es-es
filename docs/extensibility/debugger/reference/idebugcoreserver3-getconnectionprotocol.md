---
title: IDebugCoreServer3::GetConnectionProtocol ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d60bb8eb333e117290c710e03faafc51f4e31a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732899"
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
Devuelve un valor que indica el protocolo que se usa para comunicarse entre el servidor y el paquete de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetConnectionProtocol(
   CONNECTION_PROTOCOL* pProtocol
);
```

```csharp
int GetConnectionProtocol(
   CONNECTION_PROTOCOL[] pProtocol
);
```

## <a name="parameters"></a>Parámetros
`pProtocol`\
[fuera] Devuelve uno de los valores de la [enumeración CONNECTION_PROTOCOL.](../../../extensibility/debugger/reference/connection-protocol.md)

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)
