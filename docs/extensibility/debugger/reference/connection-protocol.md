---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d25068b71689ffbc9e472addbd6ca3663db267c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891285"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indica el protocolo que se usa para la comunicación entre un servidor de depuración y el paquete DE depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Campos
`CONNECTION_NONE`\
No se ha establecido ninguna conexión con un servidor.

`CONNECTION_UNKNOWN`\
Se ha realizado una conexión, pero es de un tipo desconocido.

`CONNECTION_LOCAL`\
La conexión es a un servidor local.

`CONNECTION_PIPE`\
La conexión se realiza a través de una canalización con nombre.

`CONNECTION_TCPIP`\
La conexión usa TCP/IP.

`CONNECTION_HTTP`\
La conexión utiliza HTTP (a través de un servidor Web).

`CONNECTION_OTHER`\
Se estableció algún otro tipo de conexión (este valor no se usa actualmente).

## <a name="remarks"></a>Notas
Estos valores se devuelven desde el método [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
