---
title: "Funci&#243;n JsObjectToInspectable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1d15b0b8-516f-4fc6-95aa-2ddd65f8ab75
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsObjectToInspectable
Desencapsula un objeto de JavaScript a un puntero `IInspectable`  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsObjectToInspectable(  
   _In_ JsValueRef value,  
   _Out_ IInspectable  **inspectable  
);  
```  
  
#### Parámetros  
 `value`  
 Un valor de JavaScript que se debería proyectar a `IInspectable`.  
  
 `inspectable`  
 Un valor `IInspectable` del objeto.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Los hosts son responsables de aplicar las reglas de subprocesos COM.  
  
 Requiere un contexto de script activo.  
  
 Esta API solo se admite en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)