---
title: "Definici&#243;n de tipo JsPromiseContinuationCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Definici&#243;n de tipo JsPromiseContinuationCallback
Una devolución de llamada de la continuación de compromiso.  
  
## Sintaxis  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parámetros  
 `task`  
  `callbackState`  
  
## Comentarios  
 El host puede especificar una devolución de llamada de continuación de compromiso en `JsSetPromiseContinuationCallback`. Si un script crea una tarea para que se ejecute más tarde, se llamará a la devolución de llamada de continuación de compromiso con la tarea y la tarea deberá colocarse en una cola FIFO, que se ejecutará cuando se acabe de ejecutar el script actual.  
  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)