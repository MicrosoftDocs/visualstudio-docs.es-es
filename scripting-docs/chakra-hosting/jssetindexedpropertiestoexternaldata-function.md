---
title: "Funci&#243;n JsSetIndexedPropertiesToExternalData | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsSetIndexedPropertiesToExternalData
Establece las propiedades indizadas de un objeto en datos externos.  Los datos externos se utilizarán como almacén de reserva para las propiedades indizadas del objeto y se accederá a ellos como una matriz con tipo.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### Parámetros  
 `object`  
 El objeto en el que se va a trabajar.  
  
 `data`  
 Los datos externos que se utilizarán como almacén de reserva para las propiedades del objeto indizado.  
  
 `arrayType`  
 El tipo de elemento de matriz en los datos externos.  
  
 `elementLength`  
 El número de elementos de matriz en los datos externos.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)