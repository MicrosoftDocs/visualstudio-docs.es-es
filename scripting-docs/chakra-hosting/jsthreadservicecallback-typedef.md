---
title: "JsThreadServiceCallback (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsThreadServiceCallback (Typedef)
Devolución de llamada del servicio del subproceso.  
  
## Sintaxis  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### Parámetros  
 callback  
 La devolución de llamada para el elemento de trabajo en segundo plano.  
  
 callbackData  
 El argumento de datos que se va a pasar a la devolución de llamada.  
  
## Comentarios  
 El host puede especificar un servicio del subproceso en segundo plano al llamar a JsCreateRuntime.  Si se especifica, los elementos de trabajo en segundo plano se pasarán al host usando esta devolución de llamada.  Se espera que el host inicie la ejecución del elemento de trabajo en segundo plano inmediatamente y devuelva true, o que devuelva false, con lo que el runtime controlará el elemento de trabajo desde el subproceso.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)