---
title: "IDebugIDECallback::DisplayMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugIDECallback::DisplayMessage"
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugIDECallback::DisplayMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Envía la cadena especificada del mensaje en la ventana de salida del depurador.  
  
## Sintaxis  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```c#  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### Parámetros  
 `szMessage`  
 \[in\]  Cadena de mensaje para mostrar en la ventana de salida del depurador.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)