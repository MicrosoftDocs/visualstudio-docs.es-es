---
title: "Funci&#243;n Math.imul (JavaScript) | Microsoft Docs"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funci&#243;n Math.imul (JavaScript)
Devuelve el producto de dos números que se tratan como enteros de 32 bits con signo.  
  
## Sintaxis  
  
```  
Math.imul(x, y);  
```  
  
#### Parámetros  
 `x`  
 Obligatorio.  Primer número.  
  
 `y`  
 Obligatorio.  Segundo número.  
  
## Comentarios  
 Esta función se usa para los compiladores como Emscripten y Mandreel, que no implementan la multiplicación de enteros de la misma manera que JavaScript.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo multiplicar números con `Math.imul`.  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]