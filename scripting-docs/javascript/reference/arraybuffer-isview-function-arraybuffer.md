---
title: "ArrayBuffer.isView (Funci&#243;n, ArrayBuffer) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ArrayBuffer.isView (Funci&#243;n, ArrayBuffer)
Determina si un objeto proporciona una vista del búfer.  
  
## Sintaxis  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### Parámetros  
 `object`  
 Requerido.  Objeto que se va a probar.  
  
## Valor devuelto  
 Es `true` si se cumple cualquiera de las condiciones siguientes:  
  
-   `object` es un objeto `DataView`.  
  
-   `object` es una matriz con tipo.  
  
 De lo contrario, el método devuelve `false`.  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo siguiente se demuestra el uso de la función `isView` para probar una matriz con tipo y un objeto `DataView`.  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)