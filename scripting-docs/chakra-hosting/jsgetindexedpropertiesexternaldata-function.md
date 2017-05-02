---
title: "Funci&#243;n JsGetIndexedPropertiesExternalData | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2c313163-3462-42fd-8dee-3dfb3ac7f43f
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsGetIndexedPropertiesExternalData
Recupera la información de datos externos de las propiedades indizadas de un objeto.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ void** data,  
   _Out_ JsTypedArrayType* arrayType,  
   _Out_ unsigned int* elementLength  
);  
```  
  
#### Parámetros  
 `object`  
 El objeto.  
  
 `data`  
 La memoria auxiliar de datos externos para las propiedades del objeto indizado.  
  
 `arrayType`  
 El tipo de elemento de matriz en los datos externos.  
  
 `elementLength`  
 El número de elementos de matriz en los datos externos.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Esta API solo se admite en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)