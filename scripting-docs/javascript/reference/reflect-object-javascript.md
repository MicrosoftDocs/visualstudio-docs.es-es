---
title: "Objeto Reflect (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Objeto Reflect (JavaScript)
Proporciona métodos para su uso en las operaciones que se interceptan.  
  
## Sintaxis  
  
```  
Reflect.[method]  
```  
  
#### Parámetros  
 `method`  
 Obligatorio.  Nombre de uno de los métodos del objeto `Reflect`.  
  
## Comentarios  
 No se pueden crear instancias del objeto Reflect con el operador `new`.  
  
 Los métodos Reflect se suelen usar con [proxies](../../javascript/reference/proxy-object-javascript.md) porque permiten delegar al comportamiento predeterminado sin necesidad de implementar el comportamiento predeterminado en el código.  
  
 Reflect proporciona un método estático con el mismo nombre que cada captura de proxy.  Las descripciones de la tabla no son exhaustivas.  
  
|Método|Descripción|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Parecido al método [apply](../../javascript/reference/apply-method-function-javascript.md) del objeto Function.|  
|`Reflect.construct(target, args)`|Función equivalente para el operador `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Parecido a [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.deleteProperty(target, propertyName)`|Parecido a la instrucción `delete`.  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.enumerate(target)`|Parecido a la instrucción [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), la función [Object.keys](../../javascript/reference/object-keys-function-javascript.md) y [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Función equivalente para cualquier propiedad [getter](../../javascript/creating-objects-javascript.md).|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Parecido a [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.getPrototypeOf(target)`|Parecido a [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Parecido al operador `in`, [hasOwnProperty \(Método, Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) y otros métodos.  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.isExtensible(target)`|Parecido a [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Parecido a [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Parecido a [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.set(target, propertyName, value, receiver)`|Parecido a usar cualquier propiedad [setter](../../javascript/creating-objects-javascript.md).  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
|`Reflect.setPrototypeOf(target, prototype)`|Parecido a [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).  Devuelve un valor booleano que indica si la llamada se realizó correctamente.|  
  
## Ejemplo  
 El ejemplo de código siguiente muestra cómo usar `Reflect.get` para escribir un proxy que bloquee las operaciones get para las propiedades que comienzan con un carácter de subrayado.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]