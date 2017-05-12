---
title: "JsStartDebugging (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartDebugging"
helpviewer_keywords: 
  - "JsStartDebugging (función)"
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsStartDebugging (Funci&#243;n)
Inicia la depuración en el contexto actual.  
  
## Sintaxis  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### Parámetros  
 `debugApplication`  
 La aplicación de depuración que se va a usar para la depuración.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 El host debe asegurarse de que `CoInitializeEx` se llama con `COINIT_MULTITHREADED` o `COINIT_APARTMENTTHREADED` al menos una vez antes de utilizar esta API  
  
 El parámetro `debugApplication` no es compatible con el modo de borde.  Para obtener más información sobre el uso de esta API en el modo de borde, consulte [Compatibilidad con motores de borde o motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)