---
title: "Operador de desplazamiento a la izquierda bit a bit (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< (operador)"
  - "<< (operador), acerca del operador <<"
  - "operadores bit a bit, operador de desplazamiento a la izquierda"
  - "operadores de desplazamiento a la izquierda"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador de desplazamiento a la izquierda bit a bit (&lt;&lt;) (JavaScript)
Desplaza los bits de una expresión hacia la izquierda.  
  
## Sintaxis  
  
```  
  
result = expression1 << expression2  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## Comentarios  
 El operador **\<\<** desplaza los bits de *expression1* hacia la izquierda el número de bits especificado en *expression2*.  Por ejemplo:  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 La variable *temp* tiene un valor igual a 56 porque 14 \(00001110 en sistema binario\) desplazado hacia la izquierda dos bits es igual a 56 \(00111000 en sistema binario\).  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación y desplazamiento a la izquierda \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de desplazamiento a la derecha bit a bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)