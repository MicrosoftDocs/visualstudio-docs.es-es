---
title: Reverse (método) (JavaScript) | Documentos de Microsoft
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
- reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639715"
---
# <a name="reverse-method-javascript"></a>reverse (Método de JavaScript)
Invierte los elementos de un `Array`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Cualquier objeto `Array`.  
  
## <a name="return-value"></a>Valor devuelto  
 La matriz inversa.  
  
## <a name="remarks"></a>Comentarios  
 Requerido `arrayObj` referencia es un `Array` objeto.  
  
 El `reverse` método invierte los elementos de un `Array` objeto en su lugar. No crea un nuevo `Array` objeto durante la ejecución.  
  
 Si la matriz no es contigua, la `reverse` método crea elementos de la matriz que rellenan los espacios vacíos en la matriz. Cada uno de estos elementos creados tiene el valor `undefined`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `reverse`.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [concat (Método, Array)](../../javascript/reference/concat-method-array-javascript.md)