---
title: "Operador de desplazamiento a la derecha sin signo (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> (operador)"
  - "operador de desplazamiento a la derecha sin signo (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operador de desplazamiento a la derecha sin signo (&gt;&gt;&gt;) (JavaScript)
Desplaza los bits de una expresión hacia la derecha, sin mantener el signo.  
  
## Sintaxis  
  
```  
  
result = expression1 >>> expression2  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## Comentarios  
 El operador **\>\>\>** desplaza los bits de *expression1* hacia la derecha el número de bits especificado en *expression2*.  Se rellena con ceros desde la izquierda.  Los dígitos desplazados hacia la derecha se descartan.  Por ejemplo:  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 La variable *temp* tiene un valor inicial \-14 \(11111111 11111111 11111111 11110010 en binario de complemento a dos\).  Cuando se desplaza dos bits a la derecha, el valor es igual a 1073741820 \(00111111 11111111 11111111 11111100 en binario\).  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación y desplazamiento a la derecha sin signo \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de desplazamiento a la izquierda bit a bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha bit a bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)