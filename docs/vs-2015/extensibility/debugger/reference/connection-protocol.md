---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 72ed9b8a747814d9537739c8dc27e5f113547756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561865"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indica el protocolo que se usa para la comunicación entre un servidor de depuración y el paquete DE depuración (DE).  
  
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
 No se ha establecido ninguna conexión con un servidor.  
  
 CONNECTION_UNKNOWN  
 Se ha realizado una conexión, pero es de un tipo desconocido.  
  
 CONNECTION_LOCAL  
 La conexión es a un servidor local.  
  
 CONNECTION_PIPE  
 La conexión se realiza a través de una canalización con nombre.  
  
 CONNECTION_TCPIP  
 La conexión usa TCP/IP.  
  
 CONNECTION_HTTP  
 La conexión utiliza HTTP (a través de un servidor Web).  
  
 CONNECTION_OTHER  
 Se estableció algún otro tipo de conexión (este valor no se usa actualmente).  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se devuelven desde el método [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
