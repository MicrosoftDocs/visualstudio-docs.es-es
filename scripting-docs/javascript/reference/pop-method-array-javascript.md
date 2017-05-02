---
title: "pop (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop (método)"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# pop (M&#233;todo, Array de JavaScript)
Quita el último elemento de una matriz y lo devuelve.  
  
## Sintaxis  
  
```  
  
arrayObj.pop( )  
```  
  
## Comentarios  
 Los métodos [push](../../javascript/reference/push-method-array-javascript.md) y `pop` permiten simular una pila, en la que se aplica el principio "últimas entradas, primeras salidas" \(LIFO, por sus siglas en inglés\) para almacenar datos.  
  
 La referencia `arrayObj` obligatoria es un objeto `Array`.  
  
 Si la matriz está vacía, se devuelve `undefined`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `pop`.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [push \(Método, Array\)](../../javascript/reference/push-method-array-javascript.md)