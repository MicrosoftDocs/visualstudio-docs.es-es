---
title: "for... de instrucción (JavaScript) | Documentos de Microsoft"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
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
 Obligatorio. Variable que puede ser cualquier valor de propiedad de `object`.  
  
 `object`  
 Obligatorio. Un objeto iterable, como un `Array`, `Map`, `Set`, o un objeto que implementa el [interfaces de iterador](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
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