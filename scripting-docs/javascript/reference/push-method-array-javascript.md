---
title: "push (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push (método)"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# push (M&#233;todo, Array de JavaScript)
Anexa nuevos elementos a una matriz y devuelve la nueva longitud de la matriz.  
  
## Sintaxis  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto `Array`.  
  
 `item, item2,. . ., itemN`  
 Opcional.  Nuevos elementos del objeto `Array`.  
  
## Comentarios  
 Los métodos `push` y `pop` te permiten simular una pila de objetos LIFO \(último en entrar, primero en salir\).  
  
 El método `push` anexa elementos en el orden en que aparecen.  Si uno de los argumentos es una matriz, se agrega como un único elemento.  Usa el método `concat` para combinar los elementos de dos o más matrices.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `push`.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [concat \(Método, Array\)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop \(Método, Array\)](../../javascript/reference/pop-method-array-javascript.md)