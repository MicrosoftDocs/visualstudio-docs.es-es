---
title: "Funci&#243;n Number.isNaN (n&#250;mero) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funci&#243;n Number.isNaN (n&#250;mero) (JavaScript)
Devuelve un valor booleano que indica si un valor es el valor reservado `NaN` \(no un número\).  
  
## Sintaxis  
  
```  
Number.isNaN(numValue)   
```  
  
#### Parámetros  
 `numValue`  
 Obligatorio.  Valor que se va a probar con `NaN`.  
  
## Valor devuelto  
 `true` si el valor convertido al tipo `Number` es `NaN`; en caso contrario, `false`.  
  
## Comentarios  
 Este método suele usarse para probar los valores devueltos desde los métodos `parseInt` y `parseFloat`.  
  
 `Number.isNaN` corrige los problemas con la función `isNaN` global.  `Number.isNaN` solo convierte su argumento en el tipo Number después de compararlo con `NaN`.  Por tanto, devolverá `true` solo si el argumento pasado es exactamente el mismo valor que `NaN`.  La función `isNaN` global convierte su argumento en el tipo Number antes de la comparación, que puede dar lugar a valores que no son de número que devuelven `true`, mientras que podrían no devolver `true` para `Number.isNaN`.  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)  
  
## Ejemplo  
  
```javascript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```