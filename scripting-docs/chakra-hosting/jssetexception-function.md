---
title: "JsSetException (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException (función)"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetException (Funci&#243;n)
Establece el runtime del contexto actual en un estado de excepción.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### Parámetros  
 `exception`  
 La excepción de JavaScript que se va a establecer en el runtime del contexto actual.  
  
## Valor devuelto  
 `JsNoError` si el motor se estableció en un estado de excepción; en caso contrario, un código de error.  
  
## Comentarios  
 Si el runtime del contexto actual ya está en un estado de excepción, esta API devolverá `JsErrorInExceptionState`.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)