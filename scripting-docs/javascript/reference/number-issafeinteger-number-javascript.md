---
title: "Number.isSafeInteger (n&#250;mero) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger (n&#250;mero) (JavaScript)
Devuelve un valor booleano que indica si un número puede representarse de forma segura en JavaScript.  
  
## Sintaxis  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## Valor devuelto  
 `true` si el número está entre `Number.MIN_SAFE_INTEGER` y `Number.MAX_SAFE_INTEGER`, ambos incluidos; en caso contrario, `false`.  
  
## Comentarios  
 Un entero seguro en JavaScript es un número de precisión doble IEEE\-754 antes de que se aplique redondeo.  
  
## Ejemplo  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)