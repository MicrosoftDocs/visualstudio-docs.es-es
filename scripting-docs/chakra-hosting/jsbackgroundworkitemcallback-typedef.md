---
title: "JsBackgroundWorkItemCallback (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBackgroundWorkItemCallback (Typedef)
Una devolución de llamada del elemento de trabajo en segundo plano.  
  
## Sintaxis  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### Parámetros  
 callbackData  
 Argumento de datos pasado al servicio del subproceso.  
  
## Comentarios  
 Este argumento se pasa al servicio del subproceso del host \(si se proporciona\) para permitir que el host invoque la devolución de llamada del elemento de trabajo en el subproceso en segundo plano de su elección.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)