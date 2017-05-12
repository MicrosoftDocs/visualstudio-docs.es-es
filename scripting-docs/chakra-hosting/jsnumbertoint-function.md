---
title: "Funci&#243;n JsNumberToInt | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsNumberToInt
Recupera el valor `int` de un valor numérico.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### Parámetros  
 `value`  
 El valor numérico que se va a convertir en un valor `int`.  
  
 `intValue`  
 Valor de `int`.  
  
## Valor devuelto  
  
## Comentarios  
 Esta función recupera el valor de un valor numérico y lo convierte en un valor `int`.  Se producirá un error `JsErrorInvalidArgument` si el tipo del valor no es numérico.  
  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)