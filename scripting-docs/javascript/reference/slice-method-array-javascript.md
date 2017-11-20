---
title: "slice (método, Array) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>slice (Método, Array de JavaScript)
Devuelve una sección de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Un objeto `Array`.  
  
 `start`  
 Obligatorio. El principio de la parte especificada de `arrayObj`.  
  
 `end`  
 Opcional. El final de la parte especificada de `arrayObj`.  
  
## <a name="remarks"></a>Comentarios  
 El `slice` método devuelve un `Array` objeto que contiene la parte especificada de `arrayObj`.  
  
 El `slice` método copia hacia arriba, pero no incluyen el elemento indicado por `end`. Si `start` es negativo, se trata como `length`  +  `start`, donde `length` es la longitud de la matriz. Si `end` es negativo, se trata como `length`  +  `end` donde `length` es la longitud de la matriz. Si se omite `end`, la extracción continúa hasta el final de `arrayObj`. Si `end` se produce antes de `start`, no hay elementos se copian en la nueva matriz.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `slice`. En el primer ejemplo, todos excepto el último elemento de `myArray` se copia en `newArray`. En el segundo ejemplo, solo los dos últimos elementos de `myArray` se copian en `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [slice (método, String)](../../javascript/reference/slice-method-string-javascript.md)   
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)