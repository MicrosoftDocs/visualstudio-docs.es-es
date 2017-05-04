---
title: "Definici&#243;n de tipo de JsProjectionEnqueueCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Definici&#243;n de tipo de JsProjectionEnqueueCallback
La devolución de llamada de la aplicación que JsRT llama cuando una API de proyección se completa en un subproceso que no sea el original.  
  
## Sintaxis  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parámetros  
 `jsCallback`  
 La devolución de llamada que se invocará en el subproceso original.  
  
 `jsContext`  
 El contexto de las aplicaciones.  
  
 `callbackState`  
 El contexto de JsRT que se debe pasar a `jsCallback`.  
  
## Comentarios  
 Requiere una llamada a JsSetProjectionEnqueueCallback para recibir devoluciones de llamada.  
  
 Esta API solo se admite en modo perimetral.  
  
## Requisitos  
 jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)