---
title: "Definici&#243;n de tipo JsProjectionCallbackContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Definici&#243;n de tipo JsProjectionCallbackContext
El contexto que se pasa a la devolución de llamada de la aplicación, JsProjectionEnqueueCallback, desde JsRT y es pasada de nuevo a JsRT en la devolución de llamada proporcionada, `JsProjectionCallback`, por parte de la aplicación en el subproceso correcto.  
  
## Sintaxis  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## Comentarios  
 Requiere que se llame a `JsSetProjectionEnqueueCallback` para recibir devoluciones de llamada.  
  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)