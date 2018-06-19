---
title: Número de constantes (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639205"
---
# <a name="number-constants-javascript"></a>Constantes de número (JavaScript)
Las siguientes constantes de número son propiedades del objeto `Number`.  
  
## <a name="number-object-constants"></a>Constantes de objeto Número  
 No es necesario crear el objeto `Number` para acceder a estas constantes.  
  
|Constante|Valor devuelto|  
|--------------|--------------------|  
|`Number.EPSILON`|El número más pequeño que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Igual a aproximadamente 2,2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|Número más grande que se puede representar de forma segura en JavaScript. Es igual a 9007199254740991.|  
|`Number.MAX_VALUE`|El número más grande que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Igual a aproximadamente 1,79E+308.|  
|`Number.MIN_SAFE_INTEGER`|Número más pequeño que se puede representar de forma segura en JavaScript. Es igual a-9007199254740991.|  
|`Number.MIN_VALUE`|El número más cercano a cero que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Igual a aproximadamente 5,00E-324.|  
|`Number.NaN`|Un valor que no es un número.<br /><br /> En comparaciones de igualdad, `NaN` no es igual a ningún valor, incluido él mismo. Para comprobar si un valor es equivalente a `NaN`, use la [isNaN (función)](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Un valor inferior al número negativo más grande que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] muestra los valores `NEGATIVE_INFINITY` como `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Un valor superior al número más grande que se puede representar en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] muestra los valores `POSITIVE_INFINITY` como `infinity`.|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Para `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` y `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Constantes matemáticas](../../javascript/reference/math-constants-javascript.md)   
 [Constantes de JavaScript](../../javascript/reference/javascript-constants.md)   
 [Infinity (constante)](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN (constante)](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN (Función)](../../javascript/reference/isnan-function-javascript.md)