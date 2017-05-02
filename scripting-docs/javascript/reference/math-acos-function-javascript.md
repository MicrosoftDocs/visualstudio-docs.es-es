---
title: "Math.acos (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos (método)"
  - "arcosine (método)"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.acos (Funci&#243;n de JavaScript)
Devuelve el arco coseno \(o el coseno inverso\) de un número.  
  
## Sintaxis  
  
```  
Math.acos(number)  
```  
  
#### Parámetros  
 El argumento `number` necesario es una expresión numérica.  
  
## Valor devuelto  
 Arco coseno del argumento `number`, en radianes.  
  
## Ejemplo  
 En el código siguiente se muestra cómo utilizar la función `acos`.  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## Comentarios  
 **Se aplica a**: [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Math.asin \(Función\)](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan \(Función\)](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos \(Función\)](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin \(Función\)](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan \(Función\)](../../javascript/reference/math-tan-function-javascript.md)   
 [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)