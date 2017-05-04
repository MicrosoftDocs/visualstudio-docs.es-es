---
title: "JsIdle (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIdle"
helpviewer_keywords: 
  - "JsIdle (función)"
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsIdle (Funci&#243;n)
Indica al runtime que realice el procesamiento en inactividad que sea necesario.  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### Parámetros  
 `nextIdleTick`  
 El siguiente paso del sistema en el que habrá más tareas inactivas que realizar.  Puede ser NULL.  Devuelve el número de pasos máximo si no hay ninguna tarea inactiva próxima que realizar.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 Si se ha habilitado el procesamiento en inactividad para el runtime actual, la llamada a `JsIdle` informará a este de que el host está inactivo y que el runtime puede realizar tareas de limpieza de memoria.  
  
 `JsIdle` también puede devolver el número de pasos del sistema hasta que el runtime tenga más tareas inactivas que realizar.  Si se llama a `JsIdle` antes de que haya transcurrido este número de pasos, no se realizará ningún trabajo.  
  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)