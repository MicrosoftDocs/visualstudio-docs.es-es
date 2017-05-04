---
title: "JsSerializedScriptUnloadCallback (typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptUnloadCallback (typedef)
El tiempo de ejecución llama a este typedef cuando finaliza con todos los recursos relacionados con la ejecución del script. El llamador debe liberar el origen si está cargado, el código de bytes y el contexto en este momento.  
  
## Sintaxis  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### Parámetros  
 `sourceContext`  
 El contexto se pasa a `JsParseSerializedScriptWithCallback` o `JsRunSerializedScriptWithCallback`.  
  
## Comentarios  
  
> [!WARNING]
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)