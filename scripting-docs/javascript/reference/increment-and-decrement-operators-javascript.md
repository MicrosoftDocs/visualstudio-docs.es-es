---
title: Operadores de incremento (++) y decremento (--) (JavaScript) | Documentos de Microsoft
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
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637355"
---
# <a name="increment--and-decrement----operators-javascript"></a>Operadores de incremento (++) y decremento (--) (JavaScript)
Los incrementos de operador de incremento y el operador de decremento decrementa el valor de una variable en uno.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Cualquier variable.  
  
 `variable`  
 Cualquier variable.  
  
## <a name="remarks"></a>Comentarios  
 Si el operador aparece delante de la variable, se modifica el valor antes de que se evalúa la expresión. Si el operador aparece después de la variable, se modifica el valor después de que se evalúa la expresión.  En otras palabras, dada `j = ++k;`, el valor de `j` es el valor original de `k` más uno; dado `j = k++;`, el valor de `j` es el valor original de `k`, que se incrementa después de que su valor se asigna a `j`.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)