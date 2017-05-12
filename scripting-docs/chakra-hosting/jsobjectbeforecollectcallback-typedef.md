---
title: "Definici&#243;n de tipo de JsObjectBeforeCollectCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Definici&#243;n de tipo de JsObjectBeforeCollectCallback
Una devolución de llamada a la que se llamó antes de recopilar un objeto.  
  
## Sintaxis  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parámetros  
 `ref`  
 El objeto que se va a recopilar.  
  
 `callbackState`  
 El estado pasado a `JsSetObjectBeforeCollectCallback`.  
  
## Comentarios  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)