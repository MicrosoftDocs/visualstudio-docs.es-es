---
title: "Funci&#243;n Object.is (JavaScript) | Microsoft Docs"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n Object.is (JavaScript)
Devuelve un valor que indica si dos valores son el mismo valor.  
  
## Sintaxis  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### Parámetros  
 `value1`  
 Obligatorio.  Primer valor que se va a probar.  
  
 `value2`  
 Obligatorio.  Segundo valor que se va a probar.  
  
## Valor devuelto  
 `true` si el valor es el mismo; en caso contrario, `false`.  
  
## Comentarios  
 A diferencia del operador \=\=, `Object.is` no convierte los tipos al probar los valores.  
  
 La comparación aplicada por `Object.is` es parecida a la comparación aplicada por el operador \=\=\=, solo que `Object.is` trata `Number.isNaN` como el mismo valor que `NaN`.  También trata \+0 y \-0 como valores diferentes.  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]