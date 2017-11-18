---
title: "indexOf (método, Array) (JavaScript) | Documentos de Microsoft"
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
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-array-javascript"></a>indexOf (Método, Array de JavaScript)
Devuelve el índice de la primera aparición de un valor de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. Objeto de matriz.|  
|`searchElement`|Obligatorio. El valor que se buscará en `array1`.|  
|`fromIndex`|Opcional. El índice de matriz en la que se va a comenzar la búsqueda. Si `fromIndex` es se omite, la búsqueda comienza en el índice 0.|  
  
## <a name="return-value"></a>Valor devuelto  
 El índice de la primera aparición de `searchElement` en la matriz, o -1 si `searchElement` no se encuentra.  
  
## <a name="remarks"></a>Comentarios  
 El `indexOf` método busca en una matriz con un valor especificado. El método devuelve el índice de la primera aparición, o -1 si no se encuentra el valor especificado.  
  
 La búsqueda se produce en orden de índice ascendente.  
  
 Los elementos de matriz se comparan con la `searchElement` valor por igualdad estricta, similar a la `===` operador. Para obtener más información, consulte [operadores de comparación](../../javascript/reference/comparison-operators-javascript.md).  
  
 Opcional `fromIndex` argumento especifica el índice de matriz en la que se va a comenzar la búsqueda. Si `fromIndex` es mayor que o igual que la longitud de la matriz, se devuelve -1. Si `fromIndex` es negativo, la búsqueda comienza en la longitud de la matriz más `fromIndex`.  
  
## <a name="example"></a>Ejemplo  
 Los siguientes ejemplos ilustran el uso de la `indexOf` método.  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)   
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)