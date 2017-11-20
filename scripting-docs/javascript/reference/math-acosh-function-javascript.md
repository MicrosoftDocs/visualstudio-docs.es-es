---
title: "Función Math.ACOSH (JavaScript) | Documentos de Microsoft"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Función Math.acosh (JavaScript)
Devuelve el arco coseno hiperbólico (o el coseno hiperbólico inverso) de un número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Parámetros  
 El argumento `number` necesario es una expresión numérica.  
  
## <a name="return-value"></a>Valor devuelto  
 Coseno hiperbólico inverso del argumento `number` en radianes.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo se usa la función `acosh`.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Comentarios  
 **Se aplica a**: [Math (objeto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Función Math.ACOS](../../javascript/reference/math-acos-function-javascript.md)   
 [Función Math.ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Función Math.atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Función Math.Cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Función Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Función Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Math (Objeto)](../../javascript/reference/math-object-javascript.md)