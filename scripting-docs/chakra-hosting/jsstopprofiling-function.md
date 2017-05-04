---
title: "JsStopProfiling (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStopProfiling"
helpviewer_keywords: 
  - "JsStopProfiling (función)"
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStopProfiling (Funci&#243;n)
Detiene la generación de perfiles en el contexto actual.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### Parámetros  
 `reason`  
 La razón para detener la generación de perfiles que se va a pasar a la devolución de llamada del generador de perfiles.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 No devolverá un error si la generación de perfiles no ha comenzado.  
  
 Requiere un contexto de script activo.  
  
 Esta API es compatible con aplicaciones de escritorio, pero no con aplicaciones de la Tienda.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)