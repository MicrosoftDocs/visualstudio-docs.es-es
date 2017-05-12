---
title: "Funci&#243;n JsCreateDataView | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsCreateDataView
Crea un objeto `DataView` de JavaScript.  
  
## Sintaxis  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Parámetros  
 `arrayBuffer`  
 Un objeto `ArrayBuffer` existente para utilizar como almacenamiento del objeto `DataView` de resultado.  
  
 `byteOffset`  
 Desplazamiento en bytes desde el principio de `arrayBuffer` de resultado `DataView` al que se va a hacer referencia.  
  
 `byteLength`  
 El número de bytes de ArrayBuffer de DataView de resultado al que se va a hacer referencia.  
  
 `result`  
 El nuevo objeto DataView.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo se admite en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)