---
title: "JsContextRef (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsContextRef (Typedef)
Referencia a un contexto de script.  
  
## Sintaxis  
  
```  
typedef JsRef JsContextRef;  
```  
  
## Comentarios  
 Cada contexto de script incluye su propio objeto global, que es distinto del de otros contextos de script.  
  
 Muchas de las API de hospedaje de Chakra requieren un contexto de script "activo", que se puede establecer mediante `JsSetCurrentContext`.  Las API de hospedaje de Chakra que requieran el establecimiento de un contexto actual lo indicarán explícitamente en la documentación.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)