---
title: "IDebugEvent2::GetAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2::GetAttributes"
helpviewer_keywords: 
  - "IDebugEvent2::GetAttributes"
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEvent2::GetAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene los atributos para este evento de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```c#  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### Parámetros  
 `pdwAttrib`  
 \[out\]  Una combinación de marcadores de enumeración de [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) es común a todos los eventos.  este método describe el tipo de evento; por ejemplo, es el evento sincrónico o asincrónico y es un evento que detiene.  
  
## Vea también  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)