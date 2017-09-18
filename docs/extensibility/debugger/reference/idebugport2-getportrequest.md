---
title: "IDebugPort2::GetPortRequest | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2::GetPortRequest"
helpviewer_keywords: 
  - "IDebugPort2::GetPortRequest"
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene la descripción de un puerto utilizado previamente para crear el puerto \(si está disponible\).  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```c#  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### Parámetros  
 `ppRequest`  
 \[out\]  Devuelve un objeto de [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) que representa la solicitud que se utilizó para crear el puerto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_PORT_NO_REQUEST` si un puerto no se creó con una solicitud de puerto de [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .  
  
## Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)