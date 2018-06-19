---
title: Objeto reflect (JavaScript) | Documentos de Microsoft
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640925"
---
# <a name="reflect-object-javascript"></a>Objeto Reflect (JavaScript)
Proporciona métodos para su uso en las operaciones que se interceptan.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `method`  
 Requerido. Nombre de uno de los métodos del objeto `Reflect`.  
  
## <a name="remarks"></a>Comentarios  
 No se pueden crear instancias del objeto Reflect con el operador `new`.  
  
 Métodos reflect se suelen usar con [proxy](../../javascript/reference/proxy-object-javascript.md) porque permiten delegar al comportamiento predeterminado sin necesidad de implementar el comportamiento predeterminado en el código.  
  
 Reflect proporciona un método estático con el mismo nombre que cada captura de proxy. Las descripciones de la tabla no son exhaustivas.  
  
|Método|Descripción|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Similar a la [aplicar](../../javascript/reference/apply-method-function-javascript.md) método del objeto de función.|  
|`Reflect.construct(target, args)`|Función equivalente para el operador `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Similar a [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.deleteProperty(target, propertyName)`|Parecido a la instrucción `delete`. Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.enumerate(target)`|Similar a [for.. en](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instrucción, [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) función, y [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Una función equivalente para cualquier [captador](../../javascript/creating-objects-javascript.md) propiedades.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Similar a [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md). Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.getPrototypeOf(target)`|Similar a [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Similar a la `in` (operador), [hasOwnProperty (método) (objeto)](../../javascript/reference/hasownproperty-method-object-javascript.md)y otros métodos. Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.isExtensible(target)`|Similar a [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Similar a [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Similar a [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md). Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.set(target, propertyName, value, receiver)`|Similar al uso de cualquier [establecedor](../../javascript/creating-objects-javascript.md) propiedad. Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.setPrototypeOf(target, prototype)`|Similar a [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md). Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra cómo usar `Reflect.get` para escribir un proxy que bloquee las operaciones get para las propiedades que comienzan con un carácter de subrayado.  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]