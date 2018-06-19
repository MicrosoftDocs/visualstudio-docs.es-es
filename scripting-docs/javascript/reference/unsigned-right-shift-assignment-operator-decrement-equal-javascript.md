---
title: Operador de asignación de desplazamiento a la derecha sin signo (&gt;&gt;&gt;=) (JavaScript) | Documentos de Microsoft
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
- '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641395"
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Operador de asignación de desplazamiento a la derecha sin signo (&gt;&gt;&gt;=) (JavaScript)
Desplaza a la derecha el valor de una variable por el número de bits especificados en el valor de una expresión, sin mantener el signo, y asigna el resultado a la variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expresión*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Mediante el >>> = operador es exactamente igual que las acciones siguientes:  
  
```JavaScript  
result = result >>> expression  
```  
  
 El  **>>>=**  operador desplaza los bits de *resultado* derecha por el número de bits especificado en *expresión*. Los ceros se rellenan desde la izquierda. Se descartan los dígitos desplazados a la derecha. Por ejemplo:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 La variable *temp* tiene un valor inicial de -14 (11111111 11111111 11111111 11110010 en sistema binario de complemento de dos). Cuando se desplaza dos bits a la derecha, el valor es igual a 1073741820 (00111111 11111111 11111111 11111100 en binario).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de desplazamiento a la derecha sin signo (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento bit a bit a la izquierda (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento bit a bit a la derecha (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)