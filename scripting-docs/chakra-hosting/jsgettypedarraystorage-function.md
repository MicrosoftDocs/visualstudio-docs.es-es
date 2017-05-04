---
title: "Funci&#243;n JsGetTypedArrayStorage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsGetTypedArrayStorage
Obtiene el almacenamiento de memoria subyacente utilizado por una matriz con tipo.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### Parámetros  
 `typedArray`  
 La instancia de matriz con tipo.  
  
 `buffer`  
 El búfer de la matriz.  La duración del búfer devuelto es la misma que la duración de la matriz.  El puntero de búfer no se considera una referencia a la matriz para la recolección de elementos no utilizados.  
  
 `bufferLength`  
 El número de bytes en el búfer.  
  
 `arrayType`  
 Tipo de matriz.  
  
 `elementSize`  
 El tamaño de un elemento de la matriz.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)