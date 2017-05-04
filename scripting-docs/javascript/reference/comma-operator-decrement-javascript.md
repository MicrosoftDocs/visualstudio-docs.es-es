---
title: "Operador coma (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "coma (operador)"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Operador coma (,) (JavaScript)
Hace que dos expresiones se ejecuten secuencialmente.  
  
## Sintaxis  
  
```  
  
expression1, expression2  
```  
  
## Parámetros  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## Comentarios  
 El operador `,` hace que las expresiones se ejecuten de izquierda a derecha.  Un uso común del operador `,` es en la expresión de incremento de un bucle `for`.  Por ejemplo:  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 La instrucción `for` permite solo que se ejecute una única expresión al final de cada paso en un bucle.  El operador `,` permite que varias expresiones se traten como una sola expresión, por lo que ambas variables se pueden incrementar.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)