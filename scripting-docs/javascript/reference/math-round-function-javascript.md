---
title: "Math.round (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math (objeto)"
  - "Round (método)"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.round (Funci&#243;n de JavaScript)
Devuelve una expresión numérica proporcionada, redondeada al número entero más próximo.  
  
## Sintaxis  
  
```  
  
Math.round(  
number  
)   
```  
  
## Comentarios  
 El argumento obligatorio `number` es el valor que se va a redondear al entero más próximo.  
  
 En el caso de números positivos, si la parte decimal de `number` es 0,5 o mayor, el valor devuelto es igual al menor entero mayor que `number`.  Si la parte decimal es menor que 0,5, el valor devuelto es el mayor entero menor o igual que `number`.  
  
 En el caso de números negativos, si la parte decimal es exactamente \-0,5, el valor devuelto es el menor entero que es mayor que number.  
  
 Por ejemplo, `Math.round(8.5)` devuelve 9, pero `Math.round(-8.5)` devuelve \-8.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)  
  
## Vea también  
 [Math.random \(Función\)](../../javascript/reference/math-random-function-javascript.md)