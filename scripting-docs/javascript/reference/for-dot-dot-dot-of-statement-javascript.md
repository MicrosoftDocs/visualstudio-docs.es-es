---
title: "Instrucci&#243;n for...of (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Instrucci&#243;n for...of (JavaScript)
Ejecuta una o varias instrucciones para cada valor de un iterador obtenido a partir de un objeto iterable.  
  
## Sintaxis  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## Parámetros  
 `variable`  
 Obligatorio.  Variable que puede ser cualquier valor de propiedad de `object`.  
  
 `object`  
 Obligatorio.  Objeto iterable como `Array`, `Map`, `Set` o un objeto que implementa las [interfaces de iterador](http://msdn.microsoft.com/es-es/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Opcional.  Una o varias instrucciones que se van a ejecutar para cada valor de un `object`.  Puede ser una instrucción compuesta.  
  
## Comentarios  
 Al principio de cada iteración de un bucle, el valor de `variable` es el siguiente valor de propiedad de `object`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `for...of` en una matriz.  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `for...of` en un objeto `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [for...in \(Instrucción\)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [while \(Instrucción\)](../../javascript/reference/while-statement-javascript.md)