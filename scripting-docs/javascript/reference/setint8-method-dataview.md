---
title: "setInt8 (M&#233;todo, DataView) | Microsoft Docs"
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
ms.assetid: 0a0e1450-e0c4-4778-8706-4d332442d882
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setInt8 (M&#233;todo, DataView)
Almacena un valor Int8 en el desplazamiento de bytes especificado desde el inicio de la vista.  
  
## Sintaxis  
  
```  
dataView.setInt8(byteOffset, value);   
```  
  
## Parámetros  
 `byteOffset`  
 Lugar del búfer donde se debe establecer el valor.  
  
 `value`  
 Valor que se establece.  
  
## Comentarios  
 Estos métodos producen una excepción si la escritura se va a realizar más allá del final de la vista.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el primer valor Int8 del DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt8(0, 9);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]