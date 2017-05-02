---
title: "JsSerializeScript (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSerializeScript"
helpviewer_keywords: 
  - "JsSerializeScript (función)"
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSerializeScript (Funci&#243;n)
Serializa un script analizado a un búfer que se puede reutilizar.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### Parámetros  
 `script`  
 El script que se va a serializar.  
  
 `buffer`  
 El búfer en el que se va a colocar el script serializado.  Puede ser NULL.  
  
 `bufferSize`  
 En la entrada, el tamaño del búfer, en bytes; en la salida, el tamaño del búfer, en bytes, necesario para contener el script serializado.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 `JsSerializeScript` analiza un script y, a continuación, almacena la forma analizada de este en un formato independiente del runtime.  De esta manera, el script serializado se podrá deserializar en cualquier runtime sin que sea necesario volver a analizar el script.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)