---
title: "Función Object.assign (objeto) (JavaScript) | Documentos de Microsoft"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Función Object.assign (objeto) (JavaScript)
Copia los valores de uno o varios objetos de origen en un objeto de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `target`  
 Obligatorio. Objeto en el que se copian las propiedades enumerables.  
  
 `...sources`  
 Obligatorio. Uno o varios objetos de los que se copian las propiedades enumerables.  
  
## <a name="exceptions"></a>Excepciones  
 Esta función genera un `TypeError` si se produce un error de asignación, que finaliza la operación de copia. Se producirá un `TypeError` si una propiedad de destino no se puede escribir.  
  
## <a name="remarks"></a>Comentarios  
 Esta función devuelve el objeto de destino. Solo *enumerable propio* propiedades se copian desde el objeto de origen en el objeto de destino. Puede usar esta función para fusionar mediante combinación o clonar objetos.  
  
 Los orígenes `null` o `undefined` se tratan como objetos vacíos y no aportan nada al objeto de destino.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo combinar un objeto mediante `Object.assign`.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo clonar un objeto mediante `Object.assign`.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]