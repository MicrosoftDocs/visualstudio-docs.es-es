---
title: "lastIndexOf (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], lastIndexOf (método)"
  - "lastIndexOf (método) [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# lastIndexOf (M&#233;todo, Array de JavaScript)
Devuelve el índice de la última aparición de un valor especificado de una matriz.  
  
## Sintaxis  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz en el que se va a buscar.|  
|`searchElement`|Obligatorio.  Valor que se va a buscar en `array1`.|  
|`fromIndex`|Opcional.  Índice de la matriz en el que se va a comenzar la búsqueda.  Si se omite `fromIndex`, la búsqueda comienza en el último índice de la matriz.|  
  
## Valor devuelto  
 Índice de la última aparición de `searchElement` en la matriz o \-1 si `searchElement` no se encuentra.  
  
## Comentarios  
 El método `lastIndexOf` busca en una matriz un valor especificado.  El método devuelve el índice de la primera aparición o \-1 si el valor especificado no se encuentra.  
  
 La búsqueda se lleva a cabo en orden descendente de índices \(el último miembro primero\).  Para buscar en orden ascendente, usa [indexOf \(Método, Array\)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Los elementos de la matriz se someten a una comparación de igualdad estricta con el valor `searchElement`, de forma parecida a la comparación creada por el operador `===`.  Para obtener más información, consulta [Operadores de comparación](../../javascript/reference/comparison-operators-javascript.md).  
  
 El argumento `fromIndex` opcional especifica el índice de la matriz en el que comenzará la búsqueda.  Si `fromIndex` es mayor o igual que la longitud de la matriz, se busca en toda la matriz.  Si `fromIndex` es negativo, la búsqueda comienza en la longitud de la matriz más `fromIndex`.  Si el índice calculado es menor que 0, se devuelve \-1.  
  
## Ejemplo  
 En los ejemplos siguientes se muestra el uso del método `lastIndexOf`.  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [indexOf \(Método, Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)