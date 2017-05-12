---
title: "Math.max (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max (método)"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.max (Funci&#243;n de JavaScript)
Devuelve el mayor de un conjunto de expresiones numéricas proporcionadas.  
  
## Sintaxis  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## Comentarios  
 Los argumentos opcionales `number1, number2, ..., numberN` son expresiones numéricas que se evaluarán.  
  
 Si no se proporciona ningún argumento, el valor devuelto es igual a [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Si algún argumento es `NaN`, el valor devuelto es también `NaN`.  
  
## Ejemplo  
 En el código siguiente se muestra cómo obtener la mayor de dos expresiones.  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Math.min \(Función\)](../../javascript/reference/math-min-function-javascript.md)