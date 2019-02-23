---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a7d8d056fb816a428d78a8e13455cf6ccdd8a90
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705838"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Indica el protocolo utilizado para la comunicación entre un servidor de depuración y el paquete de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

#### <a name="parameters"></a>Parámetros
CONNECTION_NONE sin conexión se realizó en un servidor.

Se ha realizado CONNECTION_UNKNOWN una conexión, pero es de tipo desconocido.

Conexión CONNECTION_LOCAL es un servidor local.

CONNECTION_PIPE conexión es a través de una canalización con nombre.

CONNECTION_TCPIP conexión usa TCP/IP.

Conexión CONNECTION_HTTP usa HTTP (a través de un servidor Web).

CONNECTION_OTHER se ha establecido algún otro tipo de conexión (este valor no se utiliza actualmente).

## <a name="remarks"></a>Comentarios
Estos valores se devuelven desde el [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
