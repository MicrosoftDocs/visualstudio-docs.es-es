---
title: Bit a bit operador OR (|) (JavaScript) | Documentos de Microsoft
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
- '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633755"
---
# <a name="bitwise-or-operator--javascript"></a>Operador OR bit a bit (|) (JavaScript)
Realiza una operación OR bit a bit en dos expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expression1*  
 Cualquier expresión.  
  
 *expression2*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 El **&#124;** operador examina la representación binaria de los valores de dos expresiones y realiza una operación OR bit a bit en ellos. El resultado de esta operación se comporta como sigue:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 Cada vez que cualquiera de las expresiones tiene un 1 en un dígito, el resultado tendrá un 1 en ese dígito. En caso contrario, el resultado tendrá un 0 en ese dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Bit a bit o el operador de asignación (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)