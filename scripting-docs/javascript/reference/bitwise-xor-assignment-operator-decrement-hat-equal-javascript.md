---
title: "Operador de asignaci&#243;n XOR bit a bit (^=) (JavaScript) | Microsoft Docs"
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
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= (operador)"
  - "^= (operador), acerca del operador ^="
  - "operadores de asignación, bit a bit [JavaScript]"
  - "operadores bit a bit, XOR (operador)"
  - "XOR (operador)"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador de asignaci&#243;n XOR bit a bit (^=) (JavaScript)
Realiza una operación OR exclusiva bit a bit en una variable y en una expresión, y asigna el resultado a la variable.  
  
## Sintaxis  
  
```  
  
result ^= expression  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression*  
 Cualquier expresión.  
  
## Comentarios  
 El uso del operador **^\=** es exactamente igual que si se especifica:  
  
```javascript  
result = result ^ expression  
```  
  
 El operador **^\=** examina la representación binaria de los valores de dos expresiones y realiza una operación OR exclusiva bit a bit en ellos.  El resultado de esta operación se comporta de la siguiente manera:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Si una y solo una de las expresiones tiene un 1 en un dígito, el resultado tiene un 1 en ese dígito.  De lo contrario, el resultado tiene un 0 en ese dígito.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador XOR bit a bit \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)