---
title: "Funci&#243;n Math.hypot (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funci&#243;n Math.hypot (JavaScript)
Devuelve la raíz cuadrada de la suma de los cuadrados de los argumentos.  
  
## Sintaxis  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### Parámetros  
 `value1`  
 Obligatorio.  Primer número.  
  
 `value2`  
 Opcional.  Segunda número.  
  
 `values`  
 Opcional.  Uno o varios números.  
  
## Comentarios  
 Si algún argumento es NaN, la función devuelve NaN.  Si no se proporciona ningún argumento, la función devuelve 0.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un ejemplo del uso de la función `Math.hypot`.  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]