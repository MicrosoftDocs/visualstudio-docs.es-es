---
title: "IEnumDebugAddresses::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Reset"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Reset (método)"
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método restablece la enumeración en el primer elemento.  
  
## Sintaxis  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### Parámetros  
 None  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Después de que se llame a este método, la siguiente llamada a [Siguiente](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) devuelve el primer elemento de la enumeración.  
  
## Vea también  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)