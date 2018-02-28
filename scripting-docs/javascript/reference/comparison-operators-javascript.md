---
title: "Operadores de comparación (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Operadores de comparación (JavaScript)
Devuelve un valor booleano que indica el resultado de la comparación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 `expression1`  
 Cualquier expresión.  
  
 `comparisonoperator`  
 Cualquier operador de comparación.  
  
 `expression2`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se comparan cadenas, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utiliza el valor de carácter Unicode de la expresión de cadena.  
  
 La continuación describe cómo se comportan los diferentes grupos de operadores dependiendo de los tipos y valores de `expression1` y `expression2`:  
  
 Operadores relacionales: `<`, `>`, `<=`,`>=`  
  
-   Intenta convertir ambos `expression1` y `expression2` en números.  
  
-   Si ambas expresiones son cadenas, realice una comparación de cadenas.  
  
-   Si ambas expresiones son `NaN`, return `false`.  
  
-   Cero negativo es igual a cero positivo.  
  
-   Infinito negativo es menor que cualquier valor, incluido él mismo.  
  
-   Infinito positivo es mayor que cualquier valor, incluido él mismo.  
  
 Operadores de igualdad: `==`,`!=`  
  
-   Si los tipos de las dos expresiones son diferentes, intenta convertirlos a una cadena, número o valor booleano.  
  
-   `NaN`no es igual a cualquier elemento incluido él mismo.  
  
-   Cero negativo es igual a cero positivo.  
  
-   `null`es igual a ambos `null` y `undefined`.  
  
-   Los valores se consideran iguales si son cadenas idénticas, números numéricamente equivalentes, el mismo objeto, valores booleanos idénticos, o (si diferentes tipos) pueden convertirse en una de estas situaciones.  
  
-   Cualquier otra comparación se considera distintos.  
  
 Operadores de identidad: `===`,`!==`  
  
 Estos operadores comportan igual que los operadores de igualdad, salvo que no se realiza ninguna conversión de tipos. Si los tipos de ambas expresiones no son iguales, estas expresiones siempre devuelven `false`.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)