---
title: "JsSetRuntimeMemoryAllocationCallback (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryAllocationCallback"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryAllocationCallback (función)"
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryAllocationCallback (Funci&#243;n)
Establece una devolución de llamada de asignación de memoria para el runtime especificado  
  
## Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### Parámetros  
 `runtime`  
 El runtime para el que se va a registrar la devolución de llamada de asignación.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `allocationCallback`  
 Devolución de asignación de memoria que se va a llamar para los eventos de asignación de memoria.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## Comentarios  
 El registro de una devolución de llamada de asignación de memoria hará que el runtime devuelva la llamada al host siempre que adquiera o libere memoria del sistema operativo.  Se llama a la rutina de devolución de llamada antes de que el administrador de memoria del runtime asigne un bloque de memoria.  La asignación será rechazada si la devolución de llamada devuelve false.  El administrador de memoria del runtime también invocará a la rutina de devolución de llamada después de liberar un bloque de memoria, así como después de que se produzcan errores de asignación.  
  
 La devolución de llamada se invoca en el subproceso de ejecución del runtime actual, por lo que la ejecución se bloquea hasta que se complete la devolución de llamada.  
  
 El valor devuelto de la devolución de llamada no se almacena; las asignaciones rechazadas previamente no impedirán que el runtime invoque de nuevo a la devolución de llamada más adelante para nuevas asignaciones de memoria.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)