---
title: "Operador OR bit a bit (|) (JavaScript) | Microsoft Docs"
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
  - "|"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "| (operador)"
  - "operadores bit a bit, OR (operador)"
  - "OR (operador)"
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador OR bit a bit (|) (JavaScript)
Realiza una operación OR bit a bit en dos expresiones.  
  
## Sintaxis  
  
```  
  
result = expression1 | expression2  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## Comentarios  
 El operador          **&#124;** la representación binaria de los valores de dos expresiones y realiza una operación OR bit a bit en ellos.  El resultado de esta operación se comporta de la siguiente manera:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Cada vez que cualquiera de las dos expresiones tiene un 1 en un dígito, el resultado tiene un 1 en ese dígito.  De lo contrario, el resultado tiene un 0 en ese dígito.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación y OR bit a bit \(&#124;\=\)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)