---
title: "Math.Round (función de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Math.round (Función de JavaScript)
Devuelve una expresión numérica proporcionada se redondea al entero más próximo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `number` argumento es el valor se redondea al entero más próximo.  
  
 Para los números positivos, si la parte decimal de `number` es 0,5 o mayor, el valor devuelto es igual al entero más pequeño mayor que `number`. Si la parte decimal es menor que 0,5, el valor devuelto es el entero más grande menor o igual que `number`.  
  
 Para los números negativos, si la parte decimal es exactamente de -0,5, el valor devuelto es el entero más pequeño que es mayor que el número.  
  
 Por ejemplo, `Math.round(8.5)` devuelve 9, pero `Math.round(-8.5)` devuelve -8.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math (objeto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Math.random (Función)](../../javascript/reference/math-random-function-javascript.md)