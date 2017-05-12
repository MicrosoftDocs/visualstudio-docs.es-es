---
title: "JsStringToPointer (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer (función)"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStringToPointer (Funci&#243;n)
Recupera el puntero de cadena de un valor de cadena.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### Parámetros  
 `value`  
 El valor de cadena que se va a convertir en un puntero de cadena.  
  
 `stringValue`  
 El puntero de cadena.  
  
 `stringLength`  
 La longitud de la cadena.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Esta función recupera el puntero de cadena de un valor de cadena.  Se producirá un error `JsErrorInvalidArgument` si el valor no es de tipo cadena.  La duración de la cadena devuelta será la misma que la del valor del que proviene, pero el puntero de cadena no se considera una referencia al valor \(por lo que no impedirá que se recolecte\).  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)