---
title: "CONNECTION_PROTOCOL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONNECTION_PROTOCOL"
helpviewer_keywords: 
  - "Enumeración CONNECTION_PROTOCOL"
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Indica el protocolo que se usa para comunicarse entre un servidor y el paquete de depuración de depuración.  
  
## Sintaxis  
  
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
  
```c#  
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
  
#### Parámetros  
 CONNECTION\_NONE  
 No se ha realizado ninguna conexión a un servidor.  
  
 CONNECTION\_UNKNOWN  
 Se ha creado una conexión, pero es de un tipo desconocido.  
  
 CONNECTION\_LOCAL  
 La conexión a un servidor local.  
  
 CONNECTION\_PIPE  
 La conexión a través de una canalización con nombre.  
  
 CONNECTION\_TCPIP  
 La conexión usa TCP\/IP.  
  
 CONNECTION\_HTTP  
 La conexión usa HTTP \(a través de un servidor web\).  
  
 CONNECTION\_OTHER  
 Se ha establecido algún otro tipo de conexión \(este valor no se utiliza actualmente\).  
  
## Comentarios  
 Estos valores se devuelven del método de [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)