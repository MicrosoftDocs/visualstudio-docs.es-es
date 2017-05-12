---
title: "Operador AND bit a bit (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operadores de asignación, bit a bit [JavaScript]"
  - "operador &, sobre el operador &"
  - "AND (operador)"
  - "& (operador)"
  - "operadores bit a bit, operador AND"
  - "operador &, operadores bit a bit"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operador AND bit a bit (&amp;) (JavaScript)
Realiza una operación AND bit a bit en dos expresiones de 32 bits.  
  
## Sintaxis  
  
```  
  
result = expression1 & expression2  
```  
  
## Parámetros  
 `result`  
 Resultado de la operación.  
  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## Comentarios  
 `&` realiza una operación AND bit a bit en cada uno de los bits de dos expresiones de 32 bits.  Si ambos bits son 1, el resultado es 1.  De lo contrario, el resultado es 0.  
  
|Bit1|Bit2|Valor de operación AND|  
|----------|----------|----------------------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 En los siguientes ejemplos se muestra cómo usar el operador `&`.  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación AND bit a bit \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)