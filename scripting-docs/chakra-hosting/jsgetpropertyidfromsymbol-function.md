---
title: "Funci&#243;n JsGetPropertyIdFromSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 190fe4b9-352e-4b10-9d0e-6c6bbd6363e8
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsGetPropertyIdFromSymbol
Obtiene el identificador de propiedad asociado al símbolo.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromSymbol(  
   _In_ JsValueRef symbol,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### Parámetros  
 `symbol`  
 El símbolo cuyo identificador de propiedad se está recuperando.  
  
 `propertyId`  
 El identificador de propiedad para el símbolo dado.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Los identificadores de propiedad son específicos de un contexto y no se pueden usar en todos los contextos.  
  
 Requiere un contexto de script activo.  
  
 Esta API solo se admite en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)