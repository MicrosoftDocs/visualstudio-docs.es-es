---
title: "JsNativeFunction (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsNativeFunction (Typedef)
Una devolución de llamada de función.  
  
## Sintaxis  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### Parámetros  
 destinatario  
 Objeto `Function` que representa la función que se invoca.  
  
 isConstructCall  
 Indica si se trata de una llamada normal o una llamada “nueva”.  
  
 argumentos  
 Los argumentos de la llamada.  
  
 argumentCount  
 Número de argumentos.  
  
## Valor de propiedad y valor devuelto  
 El resultado de la llamada, si lo hay.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)