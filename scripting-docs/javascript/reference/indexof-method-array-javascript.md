---
title: "indexOf (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "matrices [JavaScript], indexOf (método)"
  - "indexOf (método) [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# indexOf (M&#233;todo, Array de JavaScript)
Devuelve el índice de la primera aparición de un valor de una matriz.  
  
## Sintaxis  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`searchElement`|Obligatorio.  Valor que se va a buscar en `array1`.|  
|`fromIndex`|Opcional.  Índice de la matriz en el que se va a comenzar la búsqueda.  Si se omite `fromIndex`, la búsqueda comienza en el índice 0.|  
  
## Valor devuelto  
 Índice de la primera aparición de `searchElement` en la matriz o \-1 si `searchElement` no se encuentra.  
  
## Comentarios  
 El método `indexOf` busca en una matriz un valor especificado.  El método devuelve el índice de la primera aparición o \-1 si el valor especificado no se encuentra.  
  
 La búsqueda se realiza en orden ascendente de índice.  
  
 Los elementos de la matriz se comparan con el valor `searchElement` por igualdad estricta; esto es similar al operador `===`.  Para obtener más información, consulta [Operadores de comparación](../../javascript/reference/comparison-operators-javascript.md).  
  
 El argumento `fromIndex` opcional especifica el índice de la matriz en el que comenzará la búsqueda.  Si `fromIndex` es mayor o igual que la longitud de la matriz, se devuelve \-1.  Si `fromIndex` es negativo, la búsqueda comienza en la longitud de la matriz más `fromIndex`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `indexOf`.  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)