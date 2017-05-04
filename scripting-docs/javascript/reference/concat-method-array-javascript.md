---
title: "concat (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat (método, array)"
  - "Concat (método)"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# concat (M&#233;todo, Array de JavaScript)
Combina dos o más matrices.  
  
## Sintaxis  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## Parámetros  
 `array1`  
 Obligatorio.  Objeto `Array` al que se concatenan las demás matrices.  
  
 `item1,. . ., itemN`  
 Opcional.  Elementos adicionales que se agregarán al final de `array1`.  
  
## Comentarios  
 El método `concat` devuelve un objeto `Array` que contiene la concatenación de `array1` y cualquier otro elemento proporcionado.  
  
 Los elementos que se van a agregar \(*item1 itemN*\) a la matriz se agregan en orden empezando por el primer elemento de la lista.  Si uno de los elementos es una matriz, su contenido se agrega al final de `array1`.  Si el elemento no es una matriz, se agrega al final de la matriz como un elemento de matriz simple.  
  
 Los elementos de las matrices de origen se copian en la matriz resultante de la manera siguiente:  
  
-   Si un objeto se copia desde cualquiera de las matrices que se están concatenando con la nueva matriz, la referencia de objeto continúa apuntando al mismo objeto.  Un cambio en la nueva matriz o en la matriz original producirá un cambio en la otra.  
  
-   Si un valor numérico o alfanumérico se agrega a la nueva matriz, solo se copia el valor.  El cambio del valor en una matriz no afecta al valor de la otra matriz.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el método `concat` cuando se usa con una matriz.  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [concat \(Método, String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [join \(Método, Array\)](../../javascript/reference/join-method-array-javascript.md)