---
title: Operador de coma (,) (JavaScript) | Documentos de Microsoft
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
- '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634185"
---
# <a name="comma-operator--javascript"></a>Operador coma (,) (JavaScript)
Hace que dos expresiones se ejecuten secuencialmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 El `,` operador hace que las expresiones que se ejecutarán en orden de izquierda a derecha. Un uso común de la `,` operador está en la expresión de incremento de un `for` bucle. Por ejemplo:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 El `for` instrucción permite solo una sola expresión que se ejecutará al final de cada paso a través de un bucle. El `,` operador permite varias expresiones se traten como una sola expresión, por lo que se pueden incrementar las dos variables.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)