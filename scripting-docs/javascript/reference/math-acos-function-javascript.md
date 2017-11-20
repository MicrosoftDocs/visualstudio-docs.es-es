---
title: "Math.ACOS (función de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Math.acos (Función de JavaScript)
Devuelve el arco coseno (o el coseno inverso) de un número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Parámetros  
 El argumento `number` necesario es una expresión numérica.  
  
## <a name="return-value"></a>Valor devuelto  
 El arco coseno de los `number` argumento, en radianes.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo se usa la función `acos`.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Comentarios  
 **Se aplica a**: [Math (objeto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Función Math.ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Función Math.atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Función Math.Cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Función Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Función Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Math (Objeto)](../../javascript/reference/math-object-javascript.md)