---
title: "Definici&#243;n de tipo de JsProjectionCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Definici&#243;n de tipo de JsProjectionCallback
La devolución de llamada de JsRT debería llamarse con el contexto pasado a `JsProjectionEnqueueCallback` en el subproceso correcto.  
  
## Sintaxis  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### Parámetros  
 `jsContext`  
 Requiere que se llame a `JsSetProjectionEnqueueCallback` para recibir devoluciones de llamada.  
  
## Comentarios  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)