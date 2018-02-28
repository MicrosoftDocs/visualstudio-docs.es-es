---
title: Operador de desplazamiento a la derecha sin signo (&gt;&gt;&gt;) (JavaScript) | Documentos de Microsoft
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
- '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Operador de desplazamiento a la derecha sin signo (&gt;&gt;&gt;) (JavaScript)
Desplaza hacia la derecha los bits de una expresión, sin mantener el signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 El  **>>>**  operador desplaza los bits de *expression1* derecha por el número de bits especificado en *expression2*. Los ceros se rellenan desde la izquierda. Se descartan los dígitos desplazados a la derecha. Por ejemplo:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 La variable *temp* tiene un valor inicial -14 (11111111 11111111 11111111 11110010 en sistema binario de complemento de dos). Cuando resulte desplazadas derecha dos bits, el valor es igual a 1073741820 (00111111 11111111 11111111 11111100 en binario).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de asignación de desplazamiento a la derecha sin signo (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de desplazamiento bit a bit a la izquierda (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento bit a bit a la derecha (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)