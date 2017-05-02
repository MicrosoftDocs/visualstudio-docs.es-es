---
title: "Constantes de n&#250;mero (JavaScript) | Microsoft Docs"
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
  - "constantes [JavaScript], número"
  - "MAX_VALUE (constante) [JavaScript]"
  - "MIN_VALUE (constante) [JavaScript]"
  - "NaN (constante) [JavaScript]"
  - "NEGATIVE_INFINITY (constante) [JavaScript]"
  - "constantes de número [JavaScript]"
  - "Number.MAX_VALUE (constante) [JavaScript]"
  - "Number.MIN_VALUE (constante) [JavaScript]"
  - "Number.NaN (constante) [JavaScript]"
  - "Number.NEGATIVE_INFINITY (constante) [JavaScript]"
  - "Number.POSITIVE_INFINITY (constante) [JavaScript]"
  - "POSITIVE_INFINITY (constante) [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Constantes de n&#250;mero (JavaScript)
Las siguientes constantes de número son propiedades del objeto `Number`.  
  
## Constantes de objeto Número  
 No es necesario crear el objeto `Number` para acceder a estas constantes.  
  
|Constante|Valor devuelto|  
|---------------|--------------------|  
|`Number.EPSILON`|El número más pequeño que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Igual a aproximadamente 2,2204460492503130808472633361816E\-16.|  
|`Number.MAX_SAFE_INTEGER`|Número más grande que se puede representar de forma segura en JavaScript.  Es igual a 9007199254740991.|  
|`Number.MAX_VALUE`|El número más grande que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Igual a aproximadamente 1,79E\+308.|  
|`Number.MIN_SAFE_INTEGER`|Número más pequeño que se puede representar de forma segura en JavaScript.  Es igual a −9007199254740991.|  
|`Number.MIN_VALUE`|El número más cercano a cero que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Igual a aproximadamente 5,00E\-324.|  
|`Number.NaN`|Un valor que no es un número.<br /><br /> En comparaciones de igualdad, `NaN` no es igual a ningún valor, incluido él mismo.  Para probar si un valor es equivalente a `NaN`, use la [función isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Un valor inferior al número negativo más grande que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] muestra los valores `NEGATIVE_INFINITY` como `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Un valor superior al número más grande que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] muestra los valores `POSITIVE_INFINITY` como `infinity`.|  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Para `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` y `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)  
  
## Vea también  
 [Constantes matemáticas](../../javascript/reference/math-constants-javascript.md)   
 [Constantes de JavaScript](../../javascript/reference/javascript-constants.md)   
 [Infinity \(Constante\)](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN \(Constante\)](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN \(Función\)](../../javascript/reference/isnan-function-javascript.md)