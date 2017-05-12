---
title: "Operador de asignaci&#243;n y desplazamiento a la derecha sin signo (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>= (operador)"
  - "operadores de asignación, JavaScript"
  - "operador de asignación y desplazamiento a la derecha sin signo (>>>=)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operador de asignaci&#243;n y desplazamiento a la derecha sin signo (&gt;&gt;&gt;=) (JavaScript)
Desplaza hacia la derecha el valor de una variable el número de bits especificado en el valor de una expresión, sin mantener el signo, y asigna el resultado a la variable.  
  
## Sintaxis  
  
```  
  
result >>>= expression  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression*  
 Cualquier expresión.  
  
## Comentarios  
 El uso del operador \>\>\>\= es exactamente igual que hacer lo siguiente:  
  
```javascript  
result = result >>> expression  
```  
  
 El operador **\>\>\>\=** desplaza los bits de *result* hacia la derecha el número de bits especificado en *expression*.  Se rellena con ceros desde la izquierda.  Los dígitos desplazados hacia la derecha se descartan.  Por ejemplo:  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 La variable *temp* tiene un valor inicial de \-14 \(11111111 11111111 11111111 11110010 en binario de complemento a dos\).  Cuando se desplaza dos bits a la derecha, el valor es igual a 1073741820 \(00111111 11111111 11111111 11111100 en binario\).  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de desplazamiento a la derecha sin signo \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la izquierda bit a bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha bit a bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)