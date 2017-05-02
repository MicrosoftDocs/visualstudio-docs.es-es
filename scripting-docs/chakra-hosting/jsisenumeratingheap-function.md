---
title: "JsIsEnumeratingHeap (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsEnumeratingHeap"
helpviewer_keywords: 
  - "JsIsEnumeratingHeap (función)"
ms.assetid: 5d14518e-3153-43f2-9a9c-068580cbd54f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsIsEnumeratingHeap (Funci&#243;n)
Devuelve un valor que indica si el montón del contexto actual se está enumerando.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsIsEnumeratingHeap(  
   _Out_ bool *isEnumeratingHeap  
);  
```  
  
#### Parámetros  
 `isEnumeratingHeap`  
 Indica si el montón se está enumerando.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API es compatible con aplicaciones de escritorio, pero no con aplicaciones de la Tienda.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)