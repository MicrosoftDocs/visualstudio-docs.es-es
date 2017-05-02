---
title: "Constante BYTES_PER_ELEMENT (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: f9fb2a10-9faf-4534-9183-dad2984e74ff
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Constante BYTES_PER_ELEMENT (Uint8ClampedArray)
Tamaño en bytes de cada elemento de la matriz.  
  
## Sintaxis  
  
```javascript  
var arraySize = uint8ClampedArray.BYTES_PER_ELEMENT;  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el tamaño de los elementos de la matriz.  
  
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
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)