---
title: "subarray (M&#233;todo, Int8Array) | Microsoft Docs"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray (M&#233;todo, Int8Array)
Obtiene una nueva vista Int8Array del almacén de ArrayBuffer para esta matriz, haciendo referencia a los elementos en el inicio \(incluidos\) hasta el final \(excluidos\).  
  
## Sintaxis  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## Parámetros  
 `newInt8Array`  
 Submatriz que devuelve este método.  
  
 `begin`  
 Índice del principio de la matriz.  
  
 `end`  
 Índice del final de la matriz,  sin incluir.  
  
## Comentarios  
 Si el valor de begin o end es negativo, hace referencia a un índice contando desde el final de la matriz, no desde el principio.  Si no se especifica el valor de end, la submatriz incluye todos los elementos desde el principio hasta el final del objeto TypedArray.  El intervalo especificado por los valores de begin y end se une al intervalo de índices válido para la matriz actual.  Si la longitud calculada del nuevo TypedArray fuera negativa, se fija en cero.  El objeto TypedArray devuelto será del mismo tipo que la matriz en la que se invoca este método.  
  
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
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]