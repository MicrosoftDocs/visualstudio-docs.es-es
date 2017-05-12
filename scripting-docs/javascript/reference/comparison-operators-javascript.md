---
title: "Operadores de comparaci&#243;n (JavaScript) | Microsoft Docs"
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
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operadores de comparación, script"
  - "operador mayor que"
  - "operadores de comparación"
  - "operador mayor o igual que"
  - "operador de desigualdad"
  - "operador de identidad"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operadores de comparaci&#243;n (JavaScript)
Devuelve un valor de tipo Boolean que indica el resultado de la comparación.  
  
## Sintaxis  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## Parámetros  
 `expression1`  
 Cualquier expresión.  
  
 `comparisonoperator`  
 Cualquier operador de comparación.  
  
 `expression2`  
 Cualquier expresión.  
  
## Comentarios  
 Al comparar cadenas, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor de los caracteres Unicode de la expresión de cadena.  
  
 En el siguiente ejemplo se describe cómo se comportan los diversos grupos de operadores según los tipos y valores de `expression1` y `expression2`:  
  
 Operadores relacionales: `<`, `>`, `<=`, `>=`  
  
-   Intenta convertir `expression1` y `expression2` en números.  
  
-   Si ambas expresiones son cadenas, realiza una comparación de cadenas.  
  
-   Si cualquiera de las dos expresiones es `NaN`, devuelve `false`.  
  
-   Cero negativo es igual a cero positivo.  
  
-   Infinito negativo es menor que cualquier valor, incluido él mismo.  
  
-   Infinito positivo es mayor que cualquier valor, incluido él mismo.  
  
 Operadores de igualdad: `==`, `!=`  
  
-   Si los tipos de las dos expresiones son diferentes, intenta convertirlos en tipos String, Number o Boolean.  
  
-   `NaN` no es igual a ningún valor, incluido él mismo.  
  
-   Cero negativo es igual a cero positivo.  
  
-   `null` equivale tanto a `null` como a `undefined`.  
  
-   Los valores se consideran iguales si son cadenas idénticas, números equivalentes desde el punto de vista numérico, el mismo objeto, valores de tipo Boolean idénticos, o \(si los tipos son diferentes\) si pueden convertirse en una de estas situaciones.  
  
-   Todas las demás comparaciones se consideran desigualdades.  
  
 Operador de identidad: `===`, `!==`  
  
 Estos operadores se comportan de la misma manera que los operadores de igualdad, salvo que no se realiza ninguna conversión de tipos.  Si los tipos de las dos expresiones no son iguales, estas expresiones siempre devuelven `false`.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)