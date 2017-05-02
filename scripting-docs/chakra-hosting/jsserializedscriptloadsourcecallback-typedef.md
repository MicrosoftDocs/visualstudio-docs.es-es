---
title: "JsSerializedScriptLoadSourceCallback (typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback (typedef)
El tiempo de ejecución llama a esta typedef para cargar el código fuente del script serializado. El llamador debe mantener el búfer de script válido hasta la `JsSerializedScriptUnloadCallback`.  
  
## Sintaxis  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### Parámetros  
 `sourceContext`  
 El contexto que se pasa a `JsParseSerializedScriptWithCallback` o `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 El script que se devuelve.  
  
## Comentarios  
  
> [!WARNING]
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)