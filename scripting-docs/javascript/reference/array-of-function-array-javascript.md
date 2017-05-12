---
title: "Funci&#243;n Array.of (matriz) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funci&#243;n Array.of (matriz) (JavaScript)
Devuelve una matriz de los argumentos pasados.  
  
## Sintaxis  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### Parámetros  
 `element0,...,elementN`  
 Opcional.  Elementos que se van a colocar en la matriz.  Esto crea una matriz con n \+ 1 elementos y una longitud de n \+ 1.  
  
## Comentarios  
 Esta función es parecida a llamar a `new Array(args)`, pero `Array.of` no incluye un comportamiento especial cuando se pasa un argumento.  
  
## Ejemplo  
 En el ejemplo siguiente se crea una matriz de números pasados.  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra la diferencia entre usar `Array.of` y `new Array`.  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]