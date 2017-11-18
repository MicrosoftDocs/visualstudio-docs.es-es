---
title: "concat (método, Array) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat (Método, Array de JavaScript)
Combina dos o más matrices.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `array1`  
 Obligatorio. La `Array` objeto al que se concatenan las demás matrices.  
  
 `item1,. . ., itemN`  
 Opcional. Elementos adicionales que desea agregar al final de `array1`.  
  
## <a name="remarks"></a>Comentarios  
 El `concat` método devuelve un `Array` objeto que contiene la concatenación de `array1` y cualquier otro elemento proporcionado.  
  
 Los elementos que se va a agregarse (*item1... itemN*) a la matriz se agregan, en orden, comenzando desde el primer elemento de la lista. Si uno de los elementos es una matriz, su contenido se agrega al final de `array1`. Si el elemento es un valor que no sea una matriz, se agrega al final de la matriz como un único elemento de matriz.  
  
 Elementos de las matrices de origen se copian en la matriz resultante como sigue:  
  
-   Si un objeto se copia desde cualquiera de las matrices que se va a concatenar con la nueva matriz, la referencia de objeto continúa apuntan al mismo objeto. Un cambio produce un cambio en la nueva matriz o la matriz original en el otro.  
  
-   Si un número o valor de cadena se agrega a la nueva matriz, se copia solo el valor. Cambie el valor en una matriz no afecta al valor en la otra.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `concat` método cuando se utiliza con una matriz:  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [concat (método, String)](../../javascript/reference/concat-method-string-javascript.md)   
 [join (Método, Array)](../../javascript/reference/join-method-array-javascript.md)