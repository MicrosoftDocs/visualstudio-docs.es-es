---
title: Push (método, Array) (JavaScript) | Documentos de Microsoft
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
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639455"
---
# <a name="push-method-array-javascript"></a>push (Método, Array de JavaScript)
Anexa nuevos elementos a una matriz y devuelve la nueva longitud de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Un objeto `Array`.  
  
 `item, item2,. . ., itemN`  
 Opcional. Nuevos elementos de la `Array`.  
  
## <a name="remarks"></a>Comentarios  
 El `push` y `pop` métodos permiten simular una de últimas entradas, primero en salir pila.  
  
 El `push` método anexa los elementos en el orden en que aparecen. Si uno de los argumentos es una matriz, se agrega como un único elemento. Use la `concat` método para combinar los elementos de dos o más matrices.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `push`.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [concat (método, Array)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop (Método, Array)](../../javascript/reference/pop-method-array-javascript.md)