---
title: "getFloat64 (M&#233;todo, DataView) | Microsoft Docs"
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
ms.assetid: 347adeb6-b24c-4e7d-8b6b-8e36aacdcae1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# getFloat64 (M&#233;todo, DataView)
Obtiene el valor Float64 en el desplazamiento de bytes especificado desde el inicio de la vista.  No hay ninguna restricción de alineación; se pueden capturar valores multibyte de cualquier desplazamiento.  
  
## Sintaxis  
  
```  
var testFloat = dataView.getFloat64(byteOffset, littleEndian);   
```  
  
## Parámetros  
 `testFloat`  
 Obligatorio.  Valor Float64 que se devuelve del método.  
  
 `byteOffset`  
 Lugar del búfer donde se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional.  Si es false o undefined, se debe leer un valor big\-endian. Si no, se debe leer un valor little\-endian.  
  
## Comentarios  
 Estos métodos producen una excepción si la lectura se va a realizar más allá del final de la vista.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer valor Float64 del DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat64(0));  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]