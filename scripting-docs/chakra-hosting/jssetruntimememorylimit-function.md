---
title: "JsSetRuntimeMemoryLimit (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit (función)"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryLimit (Funci&#243;n)
Establece el límite de memoria actual para un runtime.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### Parámetros  
 `runtime`  
 El runtime cuyo límite de memoria se va a establecer.  
  
 `memoryLimit`  
 El nuevo límite de memoria del runtime, en bytes, o \-1 para no establecer ningún límite de memoria.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 El límite de memoria hará que cualquier operación que lo supere produzca un error de memoria insuficiente.  Establezca el límite de memoria para el runtime en \-1 si desea que este no tenga ningún límite de memoria.  Los nuevos runtime no tendrán límite de memoria de forma predeterminada.  Si el nuevo límite de memoria supera el uso actual, la llamada se realizará correctamente y las asignaciones futuras de este runtime producirán un error hasta que el uso de memoria del runtime descienda por debajo del límite.  
  
 El límite de memoria de un runtime se puede establecer siempre, independientemente de si el runtime está activo en otro subproceso.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)