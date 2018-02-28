---
title: Operador de desplazamiento bit a bit a la izquierda (&lt;&lt;) (JavaScript) | Documentos de Microsoft
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
- <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>Operador de desplazamiento bit a bit a la izquierda (&lt;&lt;) (JavaScript)
Izquierda desplaza los bits de una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 El  **<<**  operador desplaza los bits de *expression1* hacia la izquierda el número de bits especificado en *expression2*. Por ejemplo:  
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 La variable *temp* tiene un valor de 56 porque 14 (00001110 en sistema binario) desplazado hacia la izquierda dos bits es igual a 56 (00111000 en sistema binario).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de asignación de desplazamiento a la izquierda (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de desplazamiento bit a bit a la derecha (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)