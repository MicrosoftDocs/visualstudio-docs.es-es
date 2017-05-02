---
title: "setInt16 (M&#233;todo, DataView) | Microsoft Docs"
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
ms.assetid: 901c6cf5-63fb-45bd-9ea8-185c1d892060
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setInt16 (M&#233;todo, DataView)
Establece el valor Int16 en el desplazamiento de bytes especificado desde el inicio de la vista.  No hay ninguna restricción de alineación; se pueden establecer valores multibyte en cualquier desplazamiento.  
  
## Sintaxis  
  
```  
dataView.setInt16(byteOffset, value, littleEndian);   
```  
  
## Parámetros  
 `byteOffset`  
 Lugar del búfer donde se debe recuperar el valor.  
  
 `value`  
 Valor que se establece.  
  
 `littleEndian`  
 Opcional.  Si es false o undefined, se debe escribir un valor big\-endian. Si no, se debe escribir un valor little\-endian.  
  
## Comentarios  
 Estos métodos producen una excepción si la escritura se va a realizar más allá del final de la vista.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el primer valor Int16 del DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt16(0, 9);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]