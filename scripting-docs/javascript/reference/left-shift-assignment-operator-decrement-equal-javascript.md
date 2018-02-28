---
title: "Operador de asignación de desplazamiento a la izquierda (&lt;&lt;=) (JavaScript) | Documentos de Microsoft"
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
- <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>Operador de asignación de desplazamiento a la izquierda (&lt;&lt;=) (JavaScript)
Mueve el número especificado de bits a la izquierda y asigna el resultado a `result`. Los bits vacantes debido a la operación se rellenan con 0.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression`  
 El número de bits para mover.  
  
## <a name="remarks"></a>Comentarios  
 Mediante el `<<=` operador es lo mismo que especificar`result = result << expression`  
  
 En el siguiente ejemplo se muestra cómo usar el operador `<<=`.  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de desplazamiento bit a bit a la izquierda (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento bit a bit a la derecha (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)