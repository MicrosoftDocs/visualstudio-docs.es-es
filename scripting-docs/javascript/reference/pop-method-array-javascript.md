---
title: "POP (método, Array) (JavaScript) | Documentos de Microsoft"
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
- pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="pop-method-array-javascript"></a>pop (Método, Array de JavaScript)
Quita el último elemento de una matriz y lo devuelve.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>Comentarios  
 El [inserción](../../javascript/reference/push-method-array-javascript.md) y `pop` métodos permiten simular una pila, que utiliza el principio de la última sesión, primero en salir (LIFO) para almacenar los datos.  
  
 Requerido `arrayObj` referencia es un `Array` objeto.  
  
 Si la matriz está vacía, `undefined` se devuelve.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `pop`.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [push (Método, Array)](../../javascript/reference/push-method-array-javascript.md)