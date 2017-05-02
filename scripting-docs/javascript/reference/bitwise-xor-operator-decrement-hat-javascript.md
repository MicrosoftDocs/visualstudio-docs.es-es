---
title: "Operador XOR bit a bit (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operadores bit a bit, XOR (operador)"
  - "XOR (operador)"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador XOR bit a bit (^) (JavaScript)
Realiza una operación OR exclusiva bit a bit en dos expresiones.  
  
## Sintaxis  
  
```  
  
result = expression1 ^ expression2  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## Comentarios  
 El operador **^** examina la representación binaria de los valores de dos expresiones y realiza una operación OR exclusiva bit a bit en ellos.  El resultado de esta operación se comporta de la siguiente manera:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Si una y solo una de las expresiones tiene un 1 en un dígito, el resultado tiene un 1 en ese dígito.  De lo contrario, el resultado tiene un 0 en ese dígito.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación y XOR bit a bit \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)