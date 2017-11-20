---
title: "Operador de asignación de desplazamiento a la derecha (&gt;&gt;=) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Operador de asignación de desplazamiento a la derecha (&gt;&gt;=) (JavaScript)
Desplaza a la derecha el valor de una variable por el número de bits especificados en el valor de una expresión, manteniendo el signo, y asigna el resultado a la variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expresión*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Mediante el  **>>=**  operador es exactamente lo mismo que especificar:  
  
```JavaScript  
result = result >> expression  
```  
  
 El  **>>=**  operador desplaza los bits de *resultado* derecha por el número de bits especificado en *expresión*. El inicio de sesión de bits de *resultado* se usa para rellenar los dígitos de la izquierda. Se descartan los dígitos desplazados a la derecha. Por ejemplo, después de evaluar el código siguiente, *temp* tiene un valor de -4: 14 (11110010 en sistema binario) desplazado hacia la derecha dos bits es igual a -4 (11111100 en binario).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de desplazamiento bit a bit a la izquierda (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento bit a bit a la derecha (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador de desplazamiento a la derecha sin signo (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)