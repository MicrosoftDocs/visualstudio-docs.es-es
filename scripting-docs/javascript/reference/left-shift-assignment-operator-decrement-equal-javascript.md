---
title: "Operador de asignaci&#243;n y desplazamiento a la izquierda (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<= (operador) [JavaScript]"
  - "operador de asignación y desplazamiento a la izquierda (<<=) [JavaScript]"
  - "operadores de desplazamiento a la izquierda [JavaScript]"
  - "operadores de asignación, JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operador de asignaci&#243;n y desplazamiento a la izquierda (&lt;&lt;=) (JavaScript)
Mueve el número especificado de bits a la izquierda y asigna el resultado a `result`.  Los bits que quedan vacantes por la operación se rellenan con 0.  
  
## Sintaxis  
  
```  
  
result <<= expression  
```  
  
## Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression`  
 Número de bits del desplazamiento.  
  
## Comentarios  
 El uso del operador `<<=` es igual que si se especifica `result = result << expression`  
  
 En el siguiente ejemplo se muestra cómo usar el operador `<<=`.  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de desplazamiento a la izquierda bit a bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha bit a bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)