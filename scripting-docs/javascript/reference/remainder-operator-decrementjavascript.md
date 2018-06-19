---
title: Resto (operador) (JavaScript) | Documentos de Microsoft
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
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639575"
---
# <a name="remainder-operator-javascript"></a>Operador de resto (JavaScript)
Divide el valor de una expresión por el valor de otro y devuelve el resto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Argumentos  
 `result`  
 Cualquier variable.  
  
 `number1`  
 Cualquier expresión numérica.  
  
 `number2`  
 Cualquier expresión numérica.  
  
## <a name="remarks"></a>Comentarios  
 El operador de resto divide `number1` por `number2`y devuelve solo el resto como `result`. El inicio de sesión de `result` es el mismo que el inicio de sesión de `number1`. El valor de `result` está comprendido entre 0 y el valor absoluto de `number2`.  
  
 El código siguiente muestra cómo utilizar el operador de resto.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
