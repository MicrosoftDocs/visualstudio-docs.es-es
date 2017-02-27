---
title: "IDebugCoreServer3::GetConnectionProtocol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::GetConnectionProtocol"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetConnectionProtocol"
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::GetConnectionProtocol
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve un valor que indica el protocolo que se utiliza para la comunicación entre el servidor y el paquete de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetConnectionProtocol(  
   CONNECTION_PROTOCOL* pProtocol  
);  
```  
  
```c#  
int GetConnectionProtocol(  
   CONNECTION_PROTOCOL[] pProtocol  
);  
```  
  
#### Parámetros  
 `pProtocol`  
 \[out\]  Devuelve uno de los valores de enumeración de [CONNECTION\_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [CONNECTION\_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)