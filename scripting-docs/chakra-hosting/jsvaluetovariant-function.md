---
title: "JsValueToVariant (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant (función)"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsValueToVariant (Funci&#243;n)
Inicializa la estructura `VARIANT` pasada como una proyección de un valor de JavaScript.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### Parámetros  
 `object`  
 Un valor de JavaScript que se va a proyectar como una estructura `VARIANT`.  
  
 `variant`  
 Un puntero a una estructura `VARIANT` que se inicializará como una proyección.  
  
## Valor devuelto  
  
## Comentarios  
 La proyección `VARIANT` pueden usarla los clientes de automatización COM para llamar al objeto de JavaScript proyectado.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)