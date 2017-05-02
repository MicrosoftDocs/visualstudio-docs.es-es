---
title: "Operador Modulus (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "operador Modulus, JavaScript"
  - "% (operador) [JavaScript]"
  - "Modulo (función) [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Operador Modulus (JavaScript)
Divide el valor de una expresión por el valor de otra y devuelve el resto.  
  
## Sintaxis  
  
```  
  
result = number1 % number2  
```  
  
## Argumentos  
 `result`  
 Cualquier variable.  
  
 `number1`  
 Cualquier expresión numérica.  
  
 `number2`  
 Cualquier expresión numérica.  
  
## Comentarios  
 El operador de módulo, o resto, divide `number1` por `number2` y devuelve solamente el resto como `result`.  El signo de `result` es el mismo que el de `number1`.  El valor de `result` está entre 0 y el valor absoluto de `number2`.  
  
 En el código siguiente se muestra cómo utilizar el operador de módulo.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)