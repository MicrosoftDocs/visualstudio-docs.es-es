---
title: "Operador de asignaci&#243;n y desplazamiento a la derecha (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>= (operador) [JavaScript]"
  - "operadores de asignación, JavaScript"
  - "operadores de desplazamiento a la derecha [JavaScript]"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador de asignaci&#243;n y desplazamiento a la derecha (&gt;&gt;=) (JavaScript)
Desplaza hacia la derecha el valor de una variable el número de bits especificado en el valor de una expresión, manteniendo el signo, y asigna el resultado a la variable.  
  
## Sintaxis  
  
```  
  
result >>= expression  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression*  
 Cualquier expresión.  
  
## Comentarios  
 El uso del operador **\>\>\=** es exactamente igual que si se especifica:  
  
```javascript  
result = result >> expression  
```  
  
 El operador **\>\>\=** desplaza los bits de *result* hacia la derecha el número de bits especificado en *expression*.  El bit de signo de *result* se usa para rellenar los dígitos desde la izquierda.  Los dígitos desplazados hacia la derecha se descartan.  Por ejemplo, después de evaluarse el código siguiente, la variable *temp* tiene un valor de \-4: 14 \(11110010 en sistema binario\) desplazado hacia la derecha dos bits y es igual a \-4 \(11111100 en sistema binario\).  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de desplazamiento a la izquierda bit a bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha bit a bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)