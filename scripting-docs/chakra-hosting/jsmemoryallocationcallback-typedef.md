---
title: "JsMemoryAllocationCallback (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JsMemoryAllocationCallback (Typedef)
Rutina de devolución de llamada implementada por el usuario para los eventos de asignación de memoria.  
  
## Sintaxis  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### Parámetros  
 callbackState  
 El estado pasado a JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 El tipo de evento de asignación de tipos.  
  
 allocationSize  
 El tamaño de la asignación.  
  
## Valor de propiedad y valor devuelto  
 En el evento JsMemoryAllocate, si se devuelve true el runtime podrá continuar con la asignación.  Si se devuelve false, quiere decir que la solicitud de asignación se ha rechazado.  El valor devuelto se omite para otros eventos de asignación.  
  
## Comentarios  
 Use JsSetRuntimeMemoryAllocationCallback para registrar esta devolución de llamada.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)