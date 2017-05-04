---
title: "JsDisableRuntimeExecution (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution (función)"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisableRuntimeExecution (Funci&#243;n)
Suspende la ejecución de scripts y termina los scripts en ejecución en un runtime.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Parámetros  
 `runtime`  
 El runtime que se va a suspender.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Las llamadas a un runtime suspendido producirán errores hasta que se llame a `JsEnableRuntimeExecution`.  
  
 No se debe llamar a esta API en el subproceso en el que está activo el runtime.  Aunque el runtime se colocará en un estado suspendido, es posible que un script en ejecución no se pueda suspender inmediatamente; este script terminará tan pronto como sea posible con una excepción que no se puede detectar.  
  
 La suspensión de la ejecución en un runtime que ya está suspendido es una operación inefectiva.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)