---
title: "JsAddRef (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef (función)"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsAddRef (Funci&#243;n)
Agrega una referencia a un objeto recolectado no utilizado.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### Parámetros  
 `ref`  
 El objeto al que se va a agregar una referencia.  
  
 `count`  
 El nuevo número de referencias del objeto \(se puede pasar NULL\).  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Esta función solo debe llamarse en los identificadores `JsRef` que no se van a almacenar en alguna parte de la pila.  La llamada a `JsAddRef` garantiza que el objeto al que `JsRef` hace referencia no se liberará hasta que se llame a `JsRelease`.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)