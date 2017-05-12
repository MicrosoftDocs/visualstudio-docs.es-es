---
title: "M&#233;todo subarray (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# M&#233;todo subarray (Uint8ClampedArray)
Obtiene una nueva vista [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) del almacén de [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) para esta matriz, especificando los primeros y últimos miembros de la submatriz.  
  
## Sintaxis  
  
```javascript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## Parámetros  
 `newUint8ClampedArray`  
 Requerido.  Submatriz que devuelve este método.  
  
 `begin`  
 Opcional.  Índice del principio de la matriz.  
  
 `end`  
 Opcional.  Índice del final de la matriz,  sin incluir.  
  
## Comentarios  
 Si el valor `begin` o `end` es negativo, hace referencia a un índice contando desde el final de la matriz, no desde el principio.  Si `end` no se especifica, la submatriz contiene todos los elementos desde `begin` hasta el final de la matriz con tipo.  El intervalo especificado por los valores `begin` y `end` se fija en el intervalo de índices válido para la matriz actual.  Si la longitud calculada de la nueva matriz con tipo fuera negativa, se fija en cero.  La matriz devuelta es del mismo tipo que la matriz en la que se invoca este método.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener una submatriz de dos elementos, empezando por el primer elemento de la matriz.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [Uint8Array \(Objeto\)](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md)   
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)