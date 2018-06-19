---
title: Función Math.max (JavaScript) | Documentos de Microsoft
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
- max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638645"
---
# <a name="mathmax-function-javascript"></a>Math.max (Función de JavaScript)
Devuelve el mayor de un conjunto de expresiones numéricas proporcionadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional `number1, number2, ..., numberN` argumentos son expresiones numéricas que se debe evaluar.  
  
 Si no se proporciona ningún argumento, el valor devuelto es igual a [Number.NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Si algún argumento es `NaN`, el valor devuelto también es `NaN`.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo obtener el mayor de dos expresiones.  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Math.min (Función)](../../javascript/reference/math-min-function-javascript.md)