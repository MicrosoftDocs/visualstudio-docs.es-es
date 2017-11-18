---
title: "Object.Create (función) (JavaScript) | Documentos de Microsoft"
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectcreate-function-javascript"></a>Object.create (Función de JavaScript)
Crea un objeto que tiene el prototipo especificado y, opcionalmente, que contiene las propiedades especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prototype`  
 Obligatorio. Objeto que se va a usar como un prototipo. Puede ser `null`.  
  
 `descriptors`  
 Opcional. Un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto que contiene uno o varios descriptores de propiedad.  
  
 Una *propiedad datos* es una propiedad que puede obtener y establecer un valor. Un descriptor de propiedad de datos contiene un `value` atributo, además de `writable`, `enumerable`, y `configurable` atributos. Si no se especifican los últimos tres atributos, el valor predeterminado `false`. Un *propiedad de descriptor de acceso* llama a una función proporcionada por el usuario cada vez que el valor es recuperar o establecer. Un descriptor de propiedad de descriptor de acceso contiene un `set` atributo, un `get` atributo, o ambos. Para obtener más información, consulte [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Un nuevo objeto que tiene el prototipo interno especificado y contiene las propiedades especificadas, si existe alguno.  
  
## <a name="exceptions"></a>Excepciones  
 Un `TypeError` excepción se produce si se cumple alguna de las condiciones siguientes:  
  
-   El `prototype` argumento no es un objeto y no es `null`.  
  
-   Un descriptor de la `descriptors` argumento tiene un `value` o `writable` de atributo y tiene un `get` o `set` atributo.  
  
-   Un descriptor de la `descriptors` argumento tiene un `get` o `set` atributo que no es una función.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar esta función con un `null``prototype` parámetro para detener la cadena de prototipo. El objeto creado no tendrá ningún prototipo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un objeto mediante un `null` prototipo y agrega dos propiedades enumerables.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene el mismo prototipo interno como Object (objeto). Puede ver que tiene el mismo prototipo como un objeto creado mediante el uso de un literal de objeto. El [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) función obtiene el prototipo del objeto original. Para obtener el descriptor de propiedad del objeto, puede usar [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene el mismo prototipo interno que el objeto de forma.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.getPrototypeOf (función)](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf (método) (objeto)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Creación de objetos](../../javascript/creating-objects-javascript.md)