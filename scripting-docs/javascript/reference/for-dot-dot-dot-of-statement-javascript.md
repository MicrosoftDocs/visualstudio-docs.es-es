---
title: for... de instrucción (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2373d319347f927304c32cb47856405a1d69a6b2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454601"
---
# <a name="forof-statement-javascript"></a>Instrucción for...of (JavaScript)
Ejecuta una o varias instrucciones para cada valor de un iterador obtenido a partir de un objeto iterable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parámetros  
 `variable`  
 Requerido. Variable que puede ser cualquier valor de propiedad de `object`.  
  
 `object`  
 Requerido. Un objeto iterable, como un `Array`, `Map`, `Set`, o un objeto que implementa el [interfaces de iterador](../../javascript/advanced/iterators-and-generators-javascript.md).  
  
 `statements`  
 Opcional. Una o varias instrucciones que se van a ejecutar para cada valor de un `object`. Puede ser una instrucción compuesta.  
  
## <a name="remarks"></a>Comentarios  
 Al principio de cada iteración de un bucle, el valor de `variable` es el siguiente valor de propiedad de `object`.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `for...of` en una matriz.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `for...of` en un objeto `Map`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [for... en instrucción](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [while (Instrucción)](../../javascript/reference/while-statement-javascript.md)