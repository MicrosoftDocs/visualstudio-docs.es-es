---
title: "Constantes matem&#225;ticas (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "LN2 (constante) [JavaScript]"
  - "E (constante) [JavaScript]"
  - "LOG10E (constante) [JavaScript]"
  - "SQRT1_2 (constante) [JavaScript]"
  - "LOG2E (constante) [JavaScript]"
  - "Math.SQRT2 (constante) [JavaScript]"
  - "PI (constante) [JavaScript]"
  - "Math.LOG2E (constante) [JavaScript]"
  - "constantes [JavaScript], matemáticas"
  - "Math.E (constante) [JavaScript]"
  - "constantes de logaritmo [JavaScript]"
  - "Math.LOG10E (constante) [JavaScript]"
  - "Math.SQRT1_2 (constante) [JavaScript]"
  - "SQRT2 (constante) [JavaScript]"
  - "constantes de raíz cuadrada [JavaScript]"
  - "Math.PI (constante) [JavaScript]"
  - "constantes matemáticas [JavaScript]"
  - "LN10 (constante) [JavaScript]"
  - "Math.LN2 (constante) [JavaScript]"
  - "Math.LN10 (constante) [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Constantes matem&#225;ticas (JavaScript)
Las constantes matemáticas devuelven valores constantes que son propiedades del objeto `Math`.  
  
## Constantes del objeto Math  
 En la tabla siguiente se enumeran los valores constantes que son propiedades de [Math \(objeto\)](../../javascript/reference/math-object-javascript.md).  
  
|Constante|Descripción|Valor de aproximación|  
|---------------|-----------------|---------------------------|  
|`Math.E`|Constante matemática e.  Es el número de Euler, la base de los logaritmos naturales.|2.718|  
|`Math.LN2`|Logaritmo natural de 2.|0.693|  
|`Math.LN10`|Logaritmo natural de 10.|2.302|  
|`Math.LOG2E`|Logaritmo en la base 2 de e.|1.443|  
|`Math.LOG10E`|Logaritmo en la base 10 de e.|0.434|  
|`Math.PI`|Pi.  Es la relación entre la circunferencia de un círculo y su diámetro.|3.14159|  
|`Math.SQRT1_2`|Raíz cuadrada de 0,5 o, de forma equivalente, uno dividido entre la raíz cuadrada de 2.|0.707|  
|`Math.SQRT2`|Raíz cuadrada de 2.|1.414|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar la constante `Math.PI`.  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)  
  
## Vea también  
 [Constantes de número](../../javascript/reference/number-constants-javascript.md)   
 [Constantes de JavaScript](../../javascript/reference/javascript-constants.md)