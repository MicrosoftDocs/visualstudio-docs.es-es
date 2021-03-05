---
description: Devuelve un valor que indica el protocolo que se utiliza para la comunicación entre el servidor y el paquete de depuración.
title: 'IDebugCoreServer3:: GetConnectionProtocol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ddea336fb77691459ef3e58a7724d4e242c3be2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154735"
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
Devuelve un valor que indica el protocolo que se utiliza para la comunicación entre el servidor y el paquete de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetConnectionProtocol(
   CONNECTION_PROTOCOL* pProtocol
);
```

```csharp
int GetConnectionProtocol(
   CONNECTION_PROTOCOL[] pProtocol
);
```

## <a name="parameters"></a>Parámetros
`pProtocol`\
enuncia Devuelve uno de los valores de la enumeración [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) .

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Consulte también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)
