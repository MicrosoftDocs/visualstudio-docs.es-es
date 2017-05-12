---
title: "Funci&#243;n JsCreateNamedFunction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n JsCreateNamedFunction
Crea una nueva función de JavaScript con nombre.  
  
## Sintaxis  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### Parámetros  
 `name`  
 El nombre de esta función que se utilizará para diagnósticos y convertir en cadena.  
  
 `nativeFunction`  
 Método al que se llama cuando se invoca la función.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `function`  
 Nuevo objeto de función.  
  
## Valor devuelto  
  
## Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)