---
title: "Operador de desplazamiento a la derecha bit a bit (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> (operador)"
  - ">> (operador), acerca del operador >>"
  - ">> (operador), conjuntos de bits"
  - "operadores bit a bit, operador de desplazamiento a la derecha"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operador de desplazamiento a la derecha bit a bit (&gt;&gt;) (JavaScript)
Desplaza los bits de una expresión hacia la derecha conservando el signo.  
  
## Sintaxis  
  
```  
  
result = expression1 >> expression2  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## Comentarios  
 El operador \>\> desplaza los bits de *expression1* hacia la derecha el número de bits especificado en *expression2*.  El bit de signo de *expression1* se usa para rellenar los dígitos desde la izquierda.  Los dígitos desplazados hacia la derecha se descartan.  Por ejemplo, después de evaluar el código siguiente, la variable *temp* tiene un valor igual a \-4: \-14 \(11110010 en binario de complemento a dos\) desplazado hacia la derecha dos bits es igual a \-4 \(11111100 en binario de complemento a dos\).  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de desplazamiento a la izquierda bit a bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de asignación y desplazamiento a la derecha \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)