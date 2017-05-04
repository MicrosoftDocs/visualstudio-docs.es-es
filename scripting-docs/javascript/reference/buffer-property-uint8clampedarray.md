---
title: "Propiedad buffer (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 4b87d767-4246-4cf4-bb1d-241b3516397a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Propiedad buffer (Uint8ClampedArray)
Sólo lectura.  Obtiene el [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) al que hace referencia esta matriz.  
  
## Sintaxis  
  
```javascript  
var arrayBuffer = uint8ClampedArray.buffer;  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el objeto ArrayBuffer de la matriz.  
  
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
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md)   
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)