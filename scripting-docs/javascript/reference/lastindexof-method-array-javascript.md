---
title: "lastIndexOf (método, Array) (JavaScript) | Documentos de Microsoft"
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
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf (Método, Array de JavaScript)
Devuelve el índice de la última aparición de un valor especificado de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. El objeto de matriz para buscar.|  
|`searchElement`|Obligatorio. El valor que se buscará en `array1`.|  
|`fromIndex`|Opcional. El índice de matriz en la que se va a comenzar la búsqueda. Si `fromIndex` es se omite, la búsqueda comienza en el último índice de la matriz.|  
  
## <a name="return-value"></a>Valor devuelto  
 El índice de la última aparición de `searchElement` en la matriz, o -1 si `searchElement` no se encuentra.  
  
## <a name="remarks"></a>Comentarios  
 El `lastIndexOf` método busca en una matriz con un valor especificado. El método devuelve el índice de la primera aparición, o -1 si no se encuentra el valor especificado.  
  
 La búsqueda se produce en orden de índice descendente (de último miembro primero). Para buscar en orden ascendente, use la [indexOf (método, Array)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Los elementos de matriz se comparan con la `searchElement` valor por igualdad estricta, similar a la comparación realizada por el `===` operador. Para obtener más información, consulte [operadores de comparación](../../javascript/reference/comparison-operators-javascript.md).  
  
 Opcional `fromIndex` argumento especifica el índice de matriz en la que se va a comenzar la búsqueda. Si `fromIndex` es mayor que o igual que la longitud de la matriz, se busca la matriz entera. Si `fromIndex` es negativo, la búsqueda comienza en la longitud de la matriz más `fromIndex`. Si el índice calculado es menor que 0, se devuelve -1.  
  
## <a name="example"></a>Ejemplo  
 Los siguientes ejemplos ilustran el uso de la `lastIndexOf` método.  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [indexOf (método, Array)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)