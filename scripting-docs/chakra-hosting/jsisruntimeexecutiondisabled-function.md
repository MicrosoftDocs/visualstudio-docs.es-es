---
title: "JsIsRuntimeExecutionDisabled (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled (función)"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsIsRuntimeExecutionDisabled (Funci&#243;n)
Devuelve un valor que indica si la ejecución del script está deshabilitada en el runtime.  
  
## Sintaxis  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### Parámetros  
 `runtime`  
 Especifica el runtime que se debe comprobar si la ejecución está deshabilitada.  
  
 `isDisabled`  
 Es `true` si la ejecución está deshabilitada; en caso contrario, es `false`.  
  
## Valor devuelto  
 `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)