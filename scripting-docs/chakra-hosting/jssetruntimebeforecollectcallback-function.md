---
title: "JsSetRuntimeBeforeCollectCallback (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeBeforeCollectCallback"
helpviewer_keywords: 
  - "JsSetRuntimeBeforeCollectCallback (función)"
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeBeforeCollectCallback (Funci&#243;n)
Establece una función de devolución de llamada a la que llama el runtime antes de la recolección de elementos no utilizados.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### Parámetros  
 `runtime`  
 El runtime para el que se va a registrar la devolución de llamada de asignación.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `beforeCollectCallback`  
 La función de devolución de llamada que se establece.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 La devolución de llamada se invoca en el subproceso de ejecución del runtime actual, por lo que la ejecución se bloquea hasta que se complete la devolución de llamada.  
  
 La devolución de llamada pueden usarla los hosts para preparar la recolección de elementos no utilizados.  Por ejemplo, liberando referencias innecesarias en los objetos de Chakra.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)