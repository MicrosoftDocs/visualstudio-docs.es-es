---
title: Operador de desplazamiento a la derecha bit a bit (&gt;&gt;) (JavaScript) | Documentos de Microsoft
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
- '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634275"
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Operador de desplazamiento a la derecha bit a bit (&gt;&gt;) (JavaScript)
Desplaza hacia la derecha los bits de una expresión, manteniendo el signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 El >> operador desplaza los bits de *expression1* derecha por el número de bits especificado en *expression2*. El inicio de sesión de bits de *expression1* se usa para rellenar los dígitos de la izquierda. Se descartan los dígitos desplazados a la derecha. Por ejemplo, después de evaluar el código siguiente, *temp* tiene un valor de -4:-14 (binario de complemento 11110010 sistema en de dos) desplazado hacia la derecha dos bits es igual a -4 (binario de complemento 11111100 en de dos).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de desplazamiento bit a bit a la izquierda (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de asignación de desplazamiento a la derecha (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)