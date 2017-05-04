---
title: "sort (M&#233;todo, Array de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort (método)"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# sort (M&#233;todo, Array de JavaScript)
Ordena un objeto `Array`.  
  
## Sintaxis  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## Parámetros  
 `arrayObj`  
 Requerido.  Cualquier objeto `Array`.  
  
 `sortFunction`  
 Opcional.  Nombre de la función utilizada para determinar el orden de los elementos.  Si se omite, los elementos se ordenan de forma ascendente, siguiendo el orden del juego de caracteres ASCII.  
  
## Valor devuelto  
 Matriz ordenada.  
  
## Comentarios  
 El método `sort` ordena el objeto `Array` en contexto; no se crea ningún objeto `Array` nuevo durante la ejecución.  
  
 Si proporciona una función en el argumento `sortFunction`, debe devolver uno de los siguientes valores:  
  
-   Un valor negativo si el primer argumento pasado es menor que el segundo argumento.  
  
-   Cero si los dos argumentos son equivalentes.  
  
-   Un valor positivo si el primer argumento es mayor que el segundo argumento.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `sort`.  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]