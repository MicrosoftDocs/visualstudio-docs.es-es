---
title: "slice (M&#233;todo, ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# slice (M&#233;todo, ArrayBuffer)
Devuelve una sección de [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Sintaxis  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## Parámetros  
 `arrayBufferObj`  
 Requerido.  Objeto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) del que se copiará la sección.  
  
 `start`  
 Requerido.  Índice de bytes del principio de la sección que se copiará.  
  
 `end`  
 Opcional.  Índice de bytes del final de la sección que se copiará.  
  
## Comentarios  
 El método `slice` devuelve un objeto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) que contiene el fragmento especificado de `arrayBufferObj`.  
  
 El método `slice` se copia hasta el byte indicado en `end` \(no inclusive\).  Si `start` o `end` es negativo, el índice especificado se considera como `length` \+ `start` o `end` respectivamente, donde `length` es la longitud del objeto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  Si se omite `end`, la extracción continúa hasta el final de `arrayBufferObj`.  Si `end` sucede antes que `start`, no se copia ningún byte en el nuevo objeto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `slice`.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md)