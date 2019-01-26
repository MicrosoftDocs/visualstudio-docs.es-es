---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 6d09d751dd51306810f4d0cbb56d701859e2b183
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036477"
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
 CONNECTION_NONE  
 Se ha realizado ninguna conexión a un servidor.  
  
 CONNECTION_UNKNOWN  
 Se ha realizado una conexión, pero es de tipo desconocido.  
  
 CONNECTION_LOCAL  
 Conexión es a un servidor local.  
  
 CONNECTION_PIPE  
 La conexión es a través de una canalización con nombre.  
  
 CONNECTION_TCPIP  
 La conexión usa TCP/IP.  
  
 CONNECTION_HTTP  
 Conexión usa HTTP (a través de un servidor Web).  
  
 CONNECTION_OTHER  
 Se ha establecido algún otro tipo de conexión (este valor no se utiliza actualmente).  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se devuelven desde el [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)