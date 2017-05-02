---
title: "JsGetPropertyNameFromId (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyNameFromId"
helpviewer_keywords: 
  - "JsGetPropertyNameFromId (función)"
ms.assetid: b4ca442c-573d-4bc3-adf7-1b8d48480b3a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetPropertyNameFromId (Funci&#243;n)
Obtiene el nombre asociado al identificador de propiedad.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyNameFromId(  
   _In_ JsPropertyIdRef propertyId,  
   _Outptr_result_z_ const wchar_t **name  
);  
```  
  
#### Parámetros  
 `propertyId`  
 El identificador de propiedad cuyo nombre se va a obtener.  
  
 `name`  
 El nombre asociado al identificador de propiedad.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 El búfer devuelto es válido siempre y cuando el runtime esté activo, y no se puede usar una vez desechado este.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)