---
title: "getUint16 (M&#233;todo, DataView) | Microsoft Docs"
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
ms.assetid: 3c0d9ad8-30b0-42a3-b0fe-aa805398c396
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# getUint16 (M&#233;todo, DataView)
Obtiene el valor Uint16 en el desplazamiento de bytes especificado desde el inicio de la vista.  No hay ninguna restricción de alineación; se pueden capturar valores multibyte de cualquier desplazamiento.  
  
## Sintaxis  
  
```  
var testInt = dataView.getUint16(byteOffset, littleEndian);   
```  
  
## Parámetros  
 `testInt`  
 Obligatorio.  Valor Uint16 que se devuelve del método.  
  
 `byteOffset`  
 Lugar del búfer donde se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional.  Si es false o undefined, se debe leer un valor big\-endian. Si no, se debe leer un valor little\-endian.  
  
## Comentarios  
 Estos métodos producen una excepción si la lectura se va a realizar más allá del final de la vista.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer valor Uint16 del DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint16(0));  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]