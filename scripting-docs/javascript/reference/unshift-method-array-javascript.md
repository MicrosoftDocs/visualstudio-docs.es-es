---
title: unshift (método, Array) (JavaScript) | Documentos de Microsoft
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
- unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641045"
---
# <a name="unshift-method-array-javascript"></a>unshift (Método, Array de JavaScript)
Inserta nuevos elementos al principio de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Un objeto `Array`.  
  
 `item1, item2,. . ., itemN`  
 Opcional. Elementos que se va a insertar al principio de la `Array`.  
  
## <a name="remarks"></a>Comentarios  
 El `unshift` método inserta elementos en el inicio de una matriz, por lo que aparecen en el mismo orden en que aparecen en la lista de argumentos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `unshift`.  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [shift (Método, Array)](../../javascript/reference/shift-method-array-javascript.md)