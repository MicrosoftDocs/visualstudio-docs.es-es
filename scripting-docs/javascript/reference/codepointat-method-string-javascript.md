---
title: "M&#233;todo codePointAt (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo codePointAt (String) (JavaScript)
Devuelve el punto de código de un carácter Unicode UTF\-16.  
  
## Sintaxis  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### Parámetros  
 `stringObj`  
 Requerido.  El objeto de cadena.  
  
 `pos`  
 Requerido.  Posición del carácter.  
  
## Comentarios  
 Este método devuelve valores de punto de código, incluidos puntos de código astrales \(puntos de código con más de cuatro valores hexadecimales\), para todos los caracteres UTF\-16.  
  
 Si `pos` es menor que cero \(0\) o mayor que el tamaño de la cadena, el valor devuelto es `undefined`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `codePointAt`.  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]