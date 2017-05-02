---
title: "subarray (M&#233;todo, Float64Array) | Microsoft Docs"
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
ms.assetid: f3c24e1b-5fb2-49a1-8183-0fda33dbeaba
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray (M&#233;todo, Float64Array)
Obtiene una nueva vista Float64Array del almacén de [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md) para esta matriz, especificando los primeros y últimos miembros de la submatriz.  
  
## Sintaxis  
  
```javascript  
var newFloat64Array = float64Array.subarray(begin, end);  
```  
  
## Parámetros  
 `newFloat64Array`  
 Submatriz devuelta por este método.  
  
 `begin`  
 Índice del principio de la matriz.  
  
 `end`  
 Índice del final de la matriz.  
  
## Comentarios  
 Si el valor de `begin` o `end` es negativo, hace referencia a un índice contando desde el final de la matriz, no desde el principio.  Si `end` no se especifica, la submatriz contiene todos los elementos desde `begin` hasta el final de TypedArray.  El intervalo especificado por los valores `begin` y `end` se une al intervalo de índices válido para la matriz actual.  Si la longitud calculada de la nueva matriz con tipo fuera negativa, se une a cero.  La matriz devuelta será del mismo tipo que la matriz en la que se invoca este método.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener una submatriz con tres elementos de longitud, empezando por el primer elemento de la matriz.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]