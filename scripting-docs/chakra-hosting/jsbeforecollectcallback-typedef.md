---
title: "JsBeforeCollectCallback (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58bece47-4e6d-49e7-a93d-b6a8f9928b41
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBeforeCollectCallback (Typedef)
Una devolución de llamada que se llamó antes de la colección.  
  
## Sintaxis  
  
```  
typedef void (CALLBACK *JsBeforeCollectCallback)(  
_In_opt_ void *callbackState  
);  
```  
  
#### Parámetros  
 callbackState  
 El estado pasado a JsSetBeforeCollectCallback.  
  
## Comentarios  
 Use JsSetBeforeCollectCallback para registrar esta devolución de llamada.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)