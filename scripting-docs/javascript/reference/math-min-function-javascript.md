---
title: "Math.min (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min (método)"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.min (Funci&#243;n de JavaScript)
Devuelve la menor de un conjunto de expresiones numéricas.  
  
## Sintaxis  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## Comentarios  
 Los argumentos opcionales `number1, number2, ..., numberN` son expresiones numéricas que se evaluarán.  
  
 Si no se proporciona ningún argumento, el valor devuelto es igual a [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Si algún argumento es `NaN`, el valor devuelto es también `NaN`.  
  
## Ejemplo  
 En el código siguiente se muestra cómo obtener la menor de dos expresiones.  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Math.max \(Función\)](../../javascript/reference/math-max-function-javascript.md)