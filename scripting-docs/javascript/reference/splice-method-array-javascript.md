---
title: "splice (método, Array) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>splice (Método, Array de JavaScript)
Quita elementos de una matriz, inserta nuevos elementos en su lugar si procede y devuelve los elementos eliminados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Un objeto `Array`.  
  
 `start`  
 Obligatorio. La ubicación de base cero de la matriz desde el que se va a iniciar la eliminación de elementos.  
  
 `deleteCount`  
 Obligatorio. Número de elementos que se va a quitar.  
  
 `item1, item2,. . ., itemN`  
 Opcional. Elementos que se va a insertar en la matriz en lugar de los elementos eliminados.  
  
## <a name="remarks"></a>Comentarios  
 El `splice` método modifica `arrayObj` quitando el número especificado de elementos desde la posición `start` e insertando nuevos elementos. Los elementos eliminados se devuelven como un nuevo `Array` objeto.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo puede utilizar el método `splice`.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [slice (Método, Array)](../../javascript/reference/slice-method-array-javascript.md)