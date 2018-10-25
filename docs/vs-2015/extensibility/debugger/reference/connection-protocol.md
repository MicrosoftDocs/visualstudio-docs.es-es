---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1f5b3e788ba27a69f9b71c977ec0a459e99831f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814071"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indica el protocolo utilizado para la comunicación entre un servidor de depuración y el paquete de depuración (DE).  
  
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

