---
title: "M&#233;todo set (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# M&#233;todo set (Uint8ClampedArray)
Establece un valor o una matriz de valores.  
  
## Sintaxis  
  
```javascript  
uint8ClampedArray.set(index, value); uint8ClampedArray.set(array, offset);   
```  
  
## Parámetros  
 `index`  
 Índice de la ubicación que se va a establecer.  
  
 `value`  
 El valor que se va a establecer.  
  
 `array`  
 Matriz con o sin tipo de valores que se va a establecer.  
  
 `offset`  
 Índice de la matriz actual donde deben escribirse los valores.  
  
## Comentarios  
 Si la matriz de entrada es una matriz con tipo, las dos matrices pueden utilizar el mismo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) subyacente.  En esta situación, los valores se establecen como si todos los datos se hubiesen copiado primero en un búfer temporal que no se solapa con ninguna de las matrices y, a continuación, los datos del búfer temporal se copiasen en la matriz actual.  
  
 Si el valor de sumar el desplazamiento más la longitud de la matriz especificada está fuera de intervalo de la matriz con tipo actual, se produce una excepción.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el primer elemento de la matriz.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md)   
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)