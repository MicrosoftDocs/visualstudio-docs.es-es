---
title: "JsNumberToDouble (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsNumberToDouble"
helpviewer_keywords: 
  - "JsNumberToDouble (función)"
ms.assetid: 5f52e8b6-2b70-49a3-879a-bd83ebf2ac33
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsNumberToDouble (Funci&#243;n)
Recupera el valor `double` de un valor numérico.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsNumberToDouble(  
   _In_ JsValueRef value,  
   _Out_ double *doubleValue  
);  
```  
  
#### Parámetros  
 `value`  
 El valor numérico que se va a convertir en un valor `double`.  
  
 `doubleValue`  
 Valor de `double`.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Esta función recupera el valor de un valor numérico.  Se producirá un error `JsErrorInvalidArgument` si el tipo del valor no es numérico.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)