---
title: "JsHasException (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException (función)"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasException (Funci&#243;n)
Determina si el runtime del contexto actual está en un estado de excepción.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### Parámetros  
 `hasException`  
 Indica si el runtime del contexto actual está en el estado de excepción.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Si una llamada al runtime produce una excepción \(como resultado de ejecutar un script u otra circunstancia, como un error de conversión\), el runtime se coloca en un "estado de excepción". Las llamadas realizadas en cualquier contexto de los creados por el runtime \(salvo las API de excepción\) producirán un error `JsErrorInExceptionState` hasta que se borre la excepción.  
  
 Si el runtime del contexto actual está en el estado de la excepción cuando una devolución de llamada vuelve al motor, este automáticamente volverá a producir la excepción.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)