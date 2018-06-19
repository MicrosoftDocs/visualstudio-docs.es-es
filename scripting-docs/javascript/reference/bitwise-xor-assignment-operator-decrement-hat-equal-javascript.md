---
title: Operador de asignación y XOR bit a bit (^ =) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634035"
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>Operador de asignación XOR bit a bit (^=) (JavaScript)
Realiza una operación OR exclusiva bit a bit en una variable y una expresión y asigna el resultado a la variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expresión*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Mediante el  **^=**  operador es exactamente lo mismo que especificar:  
  
```JavaScript  
result = result ^ expression  
```  
  
 El  **^=**  operador examina la representación binaria de los valores de dos expresiones y realiza una operación OR exclusiva bit a bit en ellos. El resultado de esta operación se comporta como sigue:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Cuando una y solo una de las expresiones tiene un 1 en un dígito, el resultado tendrá un 1 en ese dígito. En caso contrario, el resultado tendrá un 0 en ese dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador XOR bit a bit (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)