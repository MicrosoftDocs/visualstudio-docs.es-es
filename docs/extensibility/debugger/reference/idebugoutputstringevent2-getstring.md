---
title: "IDebugOutputStringEvent2::GetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugOutputStringEvent2::GetString"
helpviewer_keywords: 
  - "IDebugOutputStringEvent2::GetString"
ms.assetid: f059f8e0-ad44-49ac-ba90-73576ada5e06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugOutputStringEvent2::GetString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene el mensaje mostrable.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetString(   
   BSTR* pbstrString  
);  
```  
  
```c#  
int GetString(   
   out string pbstrString  
);  
```  
  
#### Parámetros  
 `pbstrString`  
 \[out\]  devuelve el mensaje mostrable.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)