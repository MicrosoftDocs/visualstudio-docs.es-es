---
title: "JsCreateObject (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateObject"
helpviewer_keywords: 
  - "JsCreateObject (función)"
ms.assetid: 6c1d01a4-9254-443e-b974-6f0b0c861ca2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsCreateObject (Funci&#243;n)
Crea un nuevo objeto.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsCreateObject(  
   _Out_ JsValueRef *object  
);  
```  
  
#### Parámetros  
 `object`  
 El objeto nuevo.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)