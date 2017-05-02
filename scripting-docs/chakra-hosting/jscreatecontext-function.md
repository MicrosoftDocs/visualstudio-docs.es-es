---
title: "JsCreateContext (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext (función)"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateContext (Funci&#243;n)
Crea un contexto de script para ejecutar scripts.  
  
## Sintaxis  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### Parámetros  
 `runtime`  
 El runtime en el que se crea el contexto de script.  
  
 `debugApplication`  
 La aplicación de depuración que se va a usar para la depuración.  Este parámetro puede ser NULL, en cuyo caso la depuración no está habilitada para el contexto.  
  
 `newContext`  
 El contexto de script creado.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Cada contexto de script tiene su propio objeto global que está aislado del resto de contextos de script.  
  
 El parámetro `debugApplication` no es compatible con el modo de borde.  Para obtener más información sobre el uso de esta API en el modo de borde, consulte [Compatibilidad con motores de borde o motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)