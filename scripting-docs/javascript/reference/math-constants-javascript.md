---
title: "Constantes matemáticas (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Constantes matemáticas (JavaScript)
Constantes matemáticas devuelven valores constantes que son propiedades de la `Math` objeto.  
  
## <a name="math-object-constants"></a>Constantes del objeto Math  
 En la tabla siguiente se enumera los valores constantes que son propiedades de la [Math (objeto)](../../javascript/reference/math-object-javascript.md).  
  
|Constante|Descripción|Valor aproximado|  
|--------------|-----------------|-----------------------|  
|`Math.E`|La constante matemática e. Es el número de Euler, base de los logaritmos naturales.|2.718|  
|`Math.LN2`|Logaritmo natural de 2.|0.693|  
|`Math.LN10`|Logaritmo natural de 10.|2.302|  
|`Math.LOG2E`|Logaritmo en base 2 de e.|1.443|  
|`Math.LOG10E`|Logaritmo en base 10 de e.|0.434|  
|`Math.PI`|Pi. Es la proporción entre la circunferencia de un círculo y su diámetro.|3.14159|  
|`Math.SQRT1_2`|Raíz cuadrada de 0,5 o, de forma equivalente, uno dividido por la raíz cuadrada de 2.|0.707|  
|`Math.SQRT2`|Raíz cuadrada de 2.|1.414|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Math.PI` constante.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math (objeto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Constantes de número](../../javascript/reference/number-constants-javascript.md)   
 [Constantes de JavaScript](../../javascript/reference/javascript-constants.md)