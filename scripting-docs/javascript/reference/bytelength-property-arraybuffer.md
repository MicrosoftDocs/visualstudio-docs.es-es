---
title: "byteLength (Propiedad, ArrayBuffer) | Microsoft Docs"
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
ms.assetid: c158fa59-d006-4842-9d06-0fd8e630ea31
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# byteLength (Propiedad, ArrayBuffer)
Es de solo lectura.  Longitud de ArrayBuffer \(en bytes\).  
  
## Sintaxis  
  
```javascript  
var arrayLength = arrayBuffer.byteLength;  
```  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener la longitud en bytes del ArrayBuffer.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
  
        alert(buffer.byteLength);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]