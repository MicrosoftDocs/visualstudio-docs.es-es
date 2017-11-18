---
title: Math (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="math-object-javascript"></a>Math (Objeto de JavaScript)
Objeto intrínseco que proporciona funciones y constantes matemáticas básicas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>Parámetros  
 *propiedad*  
 Obligatorio. Nombre de una de las propiedades de la **matemáticas**. objeto.  
  
 *método*  
 Obligatorio. Nombre de uno de los métodos de la **matemáticas**. objeto.  
  
## <a name="remarks"></a>Comentarios  
 El **matemáticas** objeto no se puede crear mediante el **nueva** (operador) y se produce un error si intenta hacerlo. El motor de scripting lo crea al cargarse. Todos sus métodos y propiedades están disponibles para el script en todo momento.  
  
## <a name="requirements"></a>Requisitos  
 El objeto `Math` se incorporó en [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Math`.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[Math.E (constante)](../../javascript/reference/math-constants-javascript.md)|La constante matemática e. Se trata del número de Euler, base de los logaritmos naturales.|  
|[Math.LN2 (constante)](../../javascript/reference/math-constants-javascript.md)|Logaritmo natural de 2.|  
|[Math.LN10 (constante)](../../javascript/reference/math-constants-javascript.md)|Logaritmo natural de 10.|  
|[Math.LOG2E (constante)](../../javascript/reference/math-constants-javascript.md)|Logaritmo en base 2 de e.|  
|[Math.LOG10E (constante)](../../javascript/reference/math-constants-javascript.md)|Logaritmo en base 10 de e.|  
|[Math.PI (constante)](../../javascript/reference/math-constants-javascript.md)|Pi. Se trata de la relación entre la longitud de la circunferencia de un círculo y su diámetro.|  
|[Math.SQRT1_2 (constante)](../../javascript/reference/math-constants-javascript.md)|Raíz cuadrada de 0,5 o, de forma equivalente, uno dividido por la raíz cuadrada de 2.|  
|[Math.SQRT2 (constante)](../../javascript/reference/math-constants-javascript.md)|Raíz cuadrada de 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>Funciones  
 En la tabla siguiente se muestran las funciones del objeto `Math`.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[Math.abs (Función)](../../javascript/reference/math-abs-function-javascript.md)|Devuelve el valor absoluto de un número.|  
|[Math.acos (Función)](../../javascript/reference/math-acos-function-javascript.md)|Devuelve el arco coseno de un número.|  
|[Math.acosh (Función)](../../javascript/reference/math-acosh-function-javascript.md)|Devuelve el arco coseno hiperbólico (o el coseno hiperbólico inverso) de un número.|  
|[Math.asin (Función)](../../javascript/reference/math-asin-function-javascript.md)|Devuelve el arco seno de un número.|  
|[Math.asinh (Función)](../../javascript/reference/math-asinh-function-javascript.md)|Devuelve el seno hiperbólico inverso de un número.|  
|[Math.atan (Función)](../../javascript/reference/math-atan-function-javascript.md)|Devuelve el arco tangente de un número.|  
|[Math.atan2 (Función)](../../javascript/reference/math-atan2-function-javascript.md)|Devuelve el ángulo (en radianes) desde el eje X hasta un punto representado por las coordenadas x e y proporcionadas.|  
|[Math.atanh (Función)](../../javascript/reference/math-atanh-function-javascript.md)|Devuelve la tangente hiperbólica inversa de un número.|  
|[Math.ceil (Función)](../../javascript/reference/math-ceil-function-javascript.md)|Devuelve el número entero más pequeño mayor o igual que la expresión numérica proporcionada.|  
|[Math.cos (Función)](../../javascript/reference/math-cos-function-javascript.md)|Devuelve el coseno de un número.|  
|[Math.cosh (Función)](../../javascript/reference/math-cosh-function-javascript.md)|Devuelve el coseno hiperbólico de un número.|  
|[Math.exp (Función)](../../javascript/reference/math-exp-function-javascript.md)|Devuelve *e* (la base de los logaritmos naturales) elevado a una potencia.|  
|[Math.expm1 (Función)](../../javascript/reference/math-expm1-function-javascript.md)|Devuelve el resultado de restar 1 de e (la base de los logaritmos naturales) elevado a una potencia.|  
|[Math.floor (Función)](../../javascript/reference/math-floor-function-javascript.md)|Devuelve el número entero más grande menor o igual que la expresión numérica proporcionada.|  
|[Math.hypot (Función)](../../javascript/reference/math-hypot-function-javascript.md)|Devuelve la raíz cuadrada de la suma de los cuadrados de los argumentos.|  
|[Math.imul (Función)](../../javascript/reference/math-imul-function-javascript.md)|Devuelve el producto de dos números que se tratan como enteros de 32 bits con signo.|  
|[Math.log (Función)](../../javascript/reference/math-log-function-javascript.md)|Devuelve el logaritmo natural de un número.|  
|[Math.log1p (Función)](../../javascript/reference/math-log1p-function-javascript.md)|Devuelve el logaritmo natural de 1 + un número.|  
|[Math.log10 (Función)](../../javascript/reference/math-log10-function-javascript.md)|Devuelve el logaritmo en base 10 de un número.|  
|[Math.log2 (Función)](../../javascript/reference/math-log2-function-javascript.md)|Devuelve el logaritmo en base 2 de un número.|  
|[Math.max (Función)](../../javascript/reference/math-max-function-javascript.md)|Devuelve la mayor de dos expresiones numéricas proporcionadas.|  
|[Math.min (Función)](../../javascript/reference/math-min-function-javascript.md)|Devuelve el menor de dos números proporcionados.|  
|[Math.pow (Función)](../../javascript/reference/math-pow-function-javascript.md)|Devuelve el valor de una expresión base elevada a una potencia especificada.|  
|[Math.random (Función)](../../javascript/reference/math-random-function-javascript.md)|Devuelve un número pseudoaleatorio entre 0 y 1.|  
|[Math.round (Función)](../../javascript/reference/math-round-function-javascript.md)|Devuelve una expresión numérica especificada, redondeada al entero más cercano.|  
|[Math.sign (Función)](../../javascript/reference/math-sign-function-javascript.md)|Devuelve el signo de un número, que indica si el número es positivo, negativo o 0.|  
|[Math.sin (Función)](../../javascript/reference/math-sin-function-javascript.md)|Devuelve el seno de un número.|  
|[Math.sinh (Función)](../../javascript/reference/math-sinh-function-javascript.md)|Devuelve el seno hiperbólico inverso de un número.|  
|[Math.sqrt (Función)](../../javascript/reference/math-sqrt-function-javascript.md)|Devuelve la raíz cuadrada de un número.|  
|[Math.tan (Función)](../../javascript/reference/math-tan-function-javascript.md)|Devuelve la tangente de un número.|  
|[Math.tanh (Función)](../../javascript/reference/math-tanh-function-javascript.md)|Devuelve la tangente hiperbólica de un número.|  
|[Math.trunc (Función)](../../javascript/reference/math-trunc-function-javascript.md)|Devuelve la parte entera de un número, quitando los dígitos fraccionarios.|  
  
## <a name="see-also"></a>Vea también  
 [Objetos de JavaScript](../../javascript/reference/javascript-objects.md)   
 [Number (Objeto)](../../javascript/reference/number-object-javascript.md)