---
title: "JsEnableRuntimeExecution (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnableRuntimeExecution"
helpviewer_keywords: 
  - "JsEnableRuntimeExecution (función)"
ms.assetid: daa2036b-aef6-497d-a8ce-5a006b6ed13f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEnableRuntimeExecution (Funci&#243;n)
Habilita la ejecución de scripts en un runtime.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsEnableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Parámetros  
 `runtime`  
 El runtime que se va a habilitar.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Habilitar la ejecución de scripts en un runtime que ya la tiene habilitada es una operación inefectiva.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)