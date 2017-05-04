---
title: "JsMemoryEventType (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType (enumeración)"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsMemoryEventType (Enumeraci&#243;n)
Tipo de evento de devolución de llamada de asignación.  
  
## Sintaxis  
  
```  
enum JsMemoryEventType;  
```  
  
## Miembros  
  
### Valores  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`JsMemoryAllocate`|Indica una solicitud de asignación de memoria.|  
|`JsMemoryFailure`|Indica un evento de asignación con errores.|  
|`JsMemoryFree`|Indica un evento de liberación de memoria.|  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)