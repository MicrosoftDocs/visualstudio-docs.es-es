---
title: "Math.Abs (función de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathabs-function-javascript"></a>Math.abs (Función de JavaScript)
Devuelve el valor absoluto de un número (el valor sin tener en cuenta si es positivo o negativo). Por ejemplo, el valor absoluto de -5 es el mismo que el valor absoluto de 5.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Parámetros  
 Requerido `number` argumento es una expresión numérica para la que se necesita el valor absoluto.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor absoluto de la `number` argumento.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `abs`.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math (objeto)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Math (Objeto)](../../javascript/reference/math-object-javascript.md)