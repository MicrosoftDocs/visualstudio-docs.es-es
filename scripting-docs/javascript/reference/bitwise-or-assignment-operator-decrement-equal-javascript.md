---
title: "Operador de asignaci&#243;n OR bit a bit (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= (operador)"
  - "operadores de asignación, bit a bit [JavaScript]"
  - "operadores bit a bit, OR (operador)"
  - "OR (operador)"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador de asignaci&#243;n OR bit a bit (|=) (JavaScript)
Realiza una operación OR bit a bit en el valor de una variable y el valor de una expresión, y asigna el resultado a la variable.  
  
## Sintaxis  
  
```  
  
result |= expression  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression*  
 Cualquier expresión.  
  
## Comentarios  
 El uso de este operador es exactamente igual que si se especifica:  
  
```javascript  
result = result | expression  
```  
  
 El operador **&#124;\=** examina la representación binaria de los valores de *result* y *expression* y realiza una operación OR bit a bit en ellos.  El resultado de esta operación se comporta de esta forma:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Cada vez que cualquiera de las dos expresiones tiene un 1 en un dígito, el resultado tiene un 1 en ese dígito.  De lo contrario, el resultado tiene un 0 en ese dígito.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador bit a bit OR \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)