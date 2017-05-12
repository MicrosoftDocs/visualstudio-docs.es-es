---
title: "Funci&#243;n Number.isInteger (n&#250;mero) (JavaScript) | Microsoft Docs"
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n Number.isInteger (n&#250;mero) (JavaScript)
Devuelve un valor booleano que indica si un valor es un entero.  
  
## Sintaxis  
  
```  
Number.isInteger(numValue)   
```  
  
## Valor devuelto  
 `true` si el valor es un entero; en caso contrario, `false`.  
  
## Comentarios  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)  
  
## Ejemplo  
  
```javascript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```