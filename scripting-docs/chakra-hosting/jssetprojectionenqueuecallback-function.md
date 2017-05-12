---
title: "Funci&#243;n JsSetProjectionEnqueueCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funci&#243;n JsSetProjectionEnqueueCallback
Establece la devolución de llamada que se va a utilizar para invocar una finalización de proyección de vuelta al subproceso requerido de los llamadores.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### Parámetros  
 `projectionEnqueueContext`  
 La devolución de llamada que se invocará cada vez que se produzca una finalización de proyección en un subproceso en segundo plano.  
  
 `callbackState`  
 El contexto de aplicación proporcionado a `projectionEnqueueContext`.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 La llamada debería proceder de otro apartamento COM o de otro subproceso del mismo MTA.  
  
 Esta API solo es compatible en modo perimetral.  
  
> [!CAUTION]
>  Esta API no admite actualmente PInvoke.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)