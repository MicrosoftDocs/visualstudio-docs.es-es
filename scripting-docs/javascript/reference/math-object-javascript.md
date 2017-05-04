---
title: "Math (Objeto de JavaScript) | Microsoft Docs"
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
  - "Math (objeto)"
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Math (Objeto de JavaScript)
Objeto intrínseco que proporciona funciones y constantes matemáticas básicas.  
  
## Sintaxis  
  
```  
  
Math.[{property | method}]  
```  
  
## Parámetros  
 *propiedad*  
 Obligatorio.  Nombre de una de las propiedades de **Math**.  objeto.  
  
 *método*  
 Obligatorio.  Nombre de uno de los métodos de **Math**.  objeto.  
  
## Comentarios  
 El objeto **Math** no se puede crear usando el operador **new** y produce un error si intenta hacerlo.  El motor de scripting lo crea al cargarse.  Todos sus métodos y propiedades están disponibles para el script en todo momento.  
  
## Requisitos  
 El objeto `Math` se incorporó en [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  
  
<a name="js56jsobjmathprop"></a>   
## Constantes  
 En la tabla siguiente se enumeran las constantes del objeto `Math`.  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[Constante Math.E](../../javascript/reference/math-constants-javascript.md)|La constante matemática e.  Se trata del número de Euler, base de los logaritmos naturales.|  
|[Constante Math.LN2](../../javascript/reference/math-constants-javascript.md)|Logaritmo natural de 2.|  
|[Constante Math.LN10](../../javascript/reference/math-constants-javascript.md)|Logaritmo natural de 10.|  
|[Constante Math.LOG2E](../../javascript/reference/math-constants-javascript.md)|Logaritmo en base 2 de e.|  
|[Constante Math.LOG10E](../../javascript/reference/math-constants-javascript.md)|Logaritmo en base 10 de e.|  
|[Constante Math.PI](../../javascript/reference/math-constants-javascript.md)|Pi.  Se trata de la relación entre la longitud de la circunferencia de un círculo y su diámetro.|  
|[Constante Math.SQRT1\_2](../../javascript/reference/math-constants-javascript.md)|Raíz cuadrada de 0,5 o, de forma equivalente, uno dividido por la raíz cuadrada de 2.|  
|[Constante Math.SQRT2](../../javascript/reference/math-constants-javascript.md)|Raíz cuadrada de 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## Funciones  
 En la tabla siguiente se muestran las funciones del objeto `Math`.  
  
|Función|Descripción|  
|-------------|-----------------|  
|[Función Math.abs](../../javascript/reference/math-abs-function-javascript.md)|Devuelve el valor absoluto de un número.|  
|[Función Math.acos](../../javascript/reference/math-acos-function-javascript.md)|Devuelve el arco coseno de un número.|  
|[Función Math.acosh](../../javascript/reference/math-acosh-function-javascript.md)|Devuelve el arco coseno hiperbólico \(o el coseno hiperbólico inverso\) de un número.|  
|[Función Math.asin](../../javascript/reference/math-asin-function-javascript.md)|Devuelve el arco seno de un número.|  
|[Math.asinh \(función\)](../../javascript/reference/math-asinh-function-javascript.md)|Devuelve el seno hiperbólico inverso de un número.|  
|[Función Math.atan](../../javascript/reference/math-atan-function-javascript.md)|Devuelve el arco tangente de un número.|  
|[Función Math.atan2](../../javascript/reference/math-atan2-function-javascript.md)|Devuelve el ángulo \(en radianes\) desde el eje X hasta un punto representado por las coordenadas x e y proporcionadas.|  
|[Math.atanh \(función\)](../../javascript/reference/math-atanh-function-javascript.md)|Devuelve la tangente hiperbólica inversa de un número.|  
|[Función Math.ceil](../../javascript/reference/math-ceil-function-javascript.md)|Devuelve el número entero más pequeño mayor o igual que la expresión numérica proporcionada.|  
|[Función Math.cos](../../javascript/reference/math-cos-function-javascript.md)|Devuelve el coseno de un número.|  
|[Math.cosh \(función\)](../../javascript/reference/math-cosh-function-javascript.md)|Devuelve el coseno hiperbólico de un número.|  
|[Función Math.exp](../../javascript/reference/math-exp-function-javascript.md)|Devuelve *e* \(la base de los logaritmos naturales\) elevado a una potencia.|  
|[Math.expm1 \(función\)](../../javascript/reference/math-expm1-function-javascript.md)|Devuelve el resultado de restar 1 de e \(la base de los logaritmos naturales\) elevado a una potencia.|  
|[Función Math.floor](../../javascript/reference/math-floor-function-javascript.md)|Devuelve el número entero más grande menor o igual que la expresión numérica proporcionada.|  
|[Función Math.hypot](../../javascript/reference/math-hypot-function-javascript.md)|Devuelve la raíz cuadrada de la suma de los cuadrados de los argumentos.|  
|[Función Math.imul](../../javascript/reference/math-imul-function-javascript.md)|Devuelve el producto de dos números que se tratan como enteros de 32 bits con signo.|  
|[Función Math.log](../../javascript/reference/math-log-function-javascript.md)|Devuelve el logaritmo natural de un número.|  
|[Math.log1p \(función\)](../../javascript/reference/math-log1p-function-javascript.md)|Devuelve el logaritmo natural de 1 \+ un número.|  
|[Math.log10 \(función\)](../../javascript/reference/math-log10-function-javascript.md)|Devuelve el logaritmo en base 10 de un número.|  
|[Math.log2 \(función\)](../../javascript/reference/math-log2-function-javascript.md)|Devuelve el logaritmo en base 2 de un número.|  
|[Función Math.max](../../javascript/reference/math-max-function-javascript.md)|Devuelve la mayor de dos expresiones numéricas proporcionadas.|  
|[Función Math.min](../../javascript/reference/math-min-function-javascript.md)|Devuelve el menor de dos números proporcionados.|  
|[Función Math.pow](../../javascript/reference/math-pow-function-javascript.md)|Devuelve el valor de una expresión base elevada a una potencia especificada.|  
|[Función Math.random](../../javascript/reference/math-random-function-javascript.md)|Devuelve un número pseudoaleatorio entre 0 y 1.|  
|[Función Math.round](../../javascript/reference/math-round-function-javascript.md)|Devuelve una expresión numérica especificada, redondeada al entero más cercano.|  
|[Función Math.sign](../../javascript/reference/math-sign-function-javascript.md)|Devuelve el signo de un número, que indica si el número es positivo, negativo o 0.|  
|[Función Math.sin](../../javascript/reference/math-sin-function-javascript.md)|Devuelve el seno de un número.|  
|[Math.sinh \(función\)](../../javascript/reference/math-sinh-function-javascript.md)|Devuelve el seno hiperbólico inverso de un número.|  
|[Función Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Devuelve la raíz cuadrada de un número.|  
|[Función Math.tan](../../javascript/reference/math-tan-function-javascript.md)|Devuelve la tangente de un número.|  
|[Math.tanh \(función\)](../../javascript/reference/math-tanh-function-javascript.md)|Devuelve la tangente hiperbólica de un número.|  
|[Función Math.trunc](../../javascript/reference/math-trunc-function-javascript.md)|Devuelve la parte entera de un número, quitando los dígitos fraccionarios.|  
  
## Vea también  
 [Objetos de JavaScript](../../javascript/reference/javascript-objects.md)   
 [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)