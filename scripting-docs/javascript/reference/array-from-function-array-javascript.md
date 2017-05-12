---
title: "Funci&#243;n Array.from (matriz) (JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funci&#243;n Array.from (matriz) (JavaScript)
Devuelve una matriz de un objeto iterable o similar a una matriz.  
  
## Sintaxis  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### Parámetros  
 `arrayLike`  
 Obligatorio.  Objeto iterable o similar a una matriz.  
  
 `mapfn`  
 Opcional.  Función de asignación para llamar a cada elemento de `arrayLike`.  
  
 `thisArg`  
 Opcional.  Especifica el objeto `this` de la función de asignación.  
  
## Comentarios  
 El parámetro `arrayLike` debe ser un objeto con elementos indizados y una propiedad `length` o un objeto iterable, como un objeto `Set`.  
  
 Se llama a la función de asignación opcional en cada elemento de la matriz.  
  
## Ejemplo  
 El ejemplo siguiente devuelve una matriz de una colección de nodos de elemento DOM.  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## Ejemplo  
 El ejemplo siguiente devuelve una matriz de caracteres.  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## Ejemplo  
 El ejemplo siguiente devuelve una matriz de objetos contenidos en la colección.  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la sintaxis de flecha y una función de asignación para cambiar el valor de los elementos.  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]