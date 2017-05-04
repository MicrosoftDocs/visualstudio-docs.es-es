---
title: "JsGetTypedArrayInfo (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsGetTypedArrayInfo (funci&#243;n)
Obtiene las propiedades de una matriz con tipo se usan con frecuencia.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### Parámetros  
 `typedArray`  
 La instancia de matriz con tipo.  
  
 `arrayType`  
 Tipo de matriz.  
  
 `arrayBuffer`  
 El almacén de reserva `ArrayBuffer` de la matriz.  
  
 `byteOffset`  
 El desplazamiento en bytes desde el principio de arrayBuffer al que hace referencia a la matriz.  
  
 `byteLength`  
 Número de bytes de la matriz.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)