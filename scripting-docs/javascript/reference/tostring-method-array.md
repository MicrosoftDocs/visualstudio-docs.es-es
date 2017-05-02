---
title: "toString (M&#233;todo, Array) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toString (M&#233;todo, Array)
Devuelve una representación alfanumérica de una matriz.  
  
## Sintaxis  
  
```  
  
array.toString()  
```  
  
## Parámetros  
 `array`  
 Obligatorio.  Matriz que se va a representar como cadena.  
  
## Valor devuelto  
 Representación de cadena de la matriz.  
  
## Comentarios  
 Los elementos de un objeto `Array` se convierten en cadenas.  Las cadenas resultantes se concatenan y se separan por comas.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **toString** con una matriz.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]