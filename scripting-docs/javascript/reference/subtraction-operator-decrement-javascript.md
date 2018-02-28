---
title: Operador de resta (-) (JavaScript) | Documentos de Microsoft
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
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>Operador de resta (-) (JavaScript)
Resta el valor de una expresión de otra o proporciona unario de negación de una única expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable numérica.  
  
 `number`  
 Cualquier expresión numérica.  
  
 `number1`  
 Cualquier expresión numérica.  
  
 `number2`  
 Cualquier expresión numérica.  
  
## <a name="remarks"></a>Comentarios  
 En la sintaxis 1, el  **-**  es el operador de sustracción aritmética que se utiliza para buscar la diferencia entre dos números. En la sintaxis 2, el  **-**  operador se utiliza como el operador unario de negación para indicar el valor negativo de una expresión.  
  
 En la sintaxis 2, como para todos los operadores unarios, las expresiones se evalúan como sigue:  
  
-   Si se aplica a indefinido o `null` se genera expresiones, un error en tiempo de ejecución.  
  
-   Objetos se convierten en cadenas.  
  
-   Las cadenas se convierten a números si es posible. Si no es así, se produce un error de tiempo de ejecución.  
  
-   Valores booleanos se tratan como números (0 si es false, 1 si es true).  
  
 El operador se aplica al número resultante. En la sintaxis 2, si el número resultante es distinto de cero, *resultado* es igual al número resultante con el signo invertido. Si el número resultante es cero, *resultado* es cero.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de asignación y sustracción (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)