---
title: "JsRef (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRef (Typedef)
Referencia a un objeto propiedad del recolector de elementos no utilizados de Chakra.  
  
## Sintaxis  
  
```  
typedef void *JsRef;  
```  
  
## Comentarios  
 Un runtime de Chakra realizará automáticamente el seguimiento de las referencias a JsRef siempre que estas se almacenen en variables locales o en parámetros in \(por ejemplo,  en la pila\).  El almacenamiento de un JsRef en otro lugar que no sea la pila requiere llamar a JsAddRef y JsRelease para administrar la duración del objeto; de lo contrario, el recolector de elementos no utilizados puede liberar el objeto mientras está todavía en uso.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)