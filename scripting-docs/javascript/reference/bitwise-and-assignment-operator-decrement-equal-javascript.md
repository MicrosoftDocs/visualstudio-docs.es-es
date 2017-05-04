---
title: "Operador de asignaci&#243;n AND bit a bit (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= (operador)"
  - "operadores de asignación, bit a bit [JavaScript]"
  - "AND (operador)"
  - "operadores bit a bit, AND (operador)"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operador de asignaci&#243;n AND bit a bit (&amp;=) (JavaScript)
Establece el resultado de una operación AND bit a bit en el valor de una variable y el valor de una expresión.  La variable y la expresión se tratan como enteros de 32 bits.  
  
## Sintaxis  
  
```  
  
result &= expression  
```  
  
## Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression`  
 Cualquier expresión.  
  
## Comentarios  
 El uso de este operador es igual que si se especifica:  
  
```javascript  
result = result & expression  
```  
  
 [Operador AND bit a bit \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) examina la representación binaria de los valores de `result` y `expression` y realiza una operación AND bit a bit en ellos.  El resultado de esta operación se comporta de esta forma:  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 Siempre que ambas expresiones tienen un 1 en un dígito, el resultado tiene un 1 en ese dígito.  De lo contrario, el resultado tiene un 0 en ese dígito.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador AND bit a bit \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)