---
title: "isNaN (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN (método)"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# isNaN (Funci&#243;n de JavaScript)
Devuelve un valor Boolean que indica si un valor es el valor reservado `NaN`\(no es un número\).  
  
## Sintaxis  
  
```  
isNaN(numValue)   
```  
  
## Valor devuelto  
 Es `true` si el valor convertido al tipo `Number` es `NaN`; de lo contrario, es `false`.  
  
## Comentarios  
 El `numValue` obligatorio es el valor que se va a probar con `NaN`.  
  
 Este método se usa normalmente para comprobar los valores devueltos desde los métodos `parseInt` y `parseFloat`.  
  
 Asimismo, una variable que contiene `NaN` u otro valor se puede comparar consigo misma.  Si la comparación devuelve una desigualdad, es `NaN`.  Esto se debe a que `NaN` es el único valor que no es igual a sí mismo.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Ejemplo  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## Vea también  
 [isFinite \(Función\)](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN \(Constante\)](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat \(Función\)](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt \(Función\)](../../javascript/reference/parseint-function-javascript.md)