---
title: "JsGetPropertyIdFromName (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyIdFromName"
helpviewer_keywords: 
  - "JsGetPropertyIdFromName (función)"
ms.assetid: 1674906f-746a-4c62-99cd-023276683a86
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetPropertyIdFromName (Funci&#243;n)
Obtiene el identificador de propiedad asociado al nombre.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromName(  
   _In_z_ const wchar_t *name,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### Parámetros  
 `name`  
 El nombre del identificador de propiedad que se va a obtener o crear.  El nombre puede estar formado solo por dígitos.  
  
 `propertyId`  
 El identificador de propiedad de este runtime para el nombre especificado.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Los identificadores de propiedad son específicos de un contexto y no se pueden usar en todos los contextos.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)