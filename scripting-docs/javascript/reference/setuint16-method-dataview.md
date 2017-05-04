---
title: "setUint16 (M&#233;todo, DataView) | Microsoft Docs"
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint16 (M&#233;todo, DataView)
Establece el valor Uint16 en el desplazamiento de bytes especificado desde el inicio de la vista.  No hay ninguna restricción de alineación; se pueden establecer valores multibyte en cualquier desplazamiento.  
  
## Sintaxis  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## Parámetros  
 `testInt`  
 Obligatorio.  Valor Uint16 que se devuelve del método.  
  
 `value`  
 Valor que se establece.  
  
 `byteOffset`  
 Lugar del búfer donde se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional.  Si es false o undefined, se debe escribir un valor big\-endian. Si no, se debe escribir un valor little\-endian.  
  
## Comentarios  
 Estos métodos producen una excepción si la escritura se va a realizar más allá del final de la vista.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el primer valor Uint16 del DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]