---
title: Objeto de proxy (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="proxy-object-javascript"></a>Objeto proxy (JavaScript)
Habilita el comportamiento personalizado de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `target`  
 Requerido. Un objeto o una función que debe virtualizar el proxy.  
  
 `handler`  
 Requerido. Un objeto con métodos (capturas) que implementan el comportamiento personalizado.  
  
## <a name="remarks"></a>Comentarios  
 Se utiliza un objeto `Proxy` para interceptar las operaciones de bajo nivel internas en otro objeto. Los objetos proxy pueden utilizarse, entre otros fines, para la intercepción, virtualización de objetos y los registros/la generación de perfiles.  
  
 Si no se ha definido una captura para una operación determinada en el controlador para el proxy, la operación se reenvía al destino.  
  
 El objeto de controlador define los siguientes métodos (capturas) para implementar un comportamiento personalizado. Los ejemplos que se muestran aquí no son exhaustivos. Para admitir el comportamiento predeterminado condicional en el método de controlador, use los métodos de [objeto reflejar](../../javascript/reference/reflect-object-javascript.md).  
  
|Sintaxis de método de controlador (captura)|Ejemplos de uso|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|Una captura para una llamada a una función.|  
|`construct: function(target, args)`|Una captura para un constructor.|  
|`defineProperty: function(target, propertyName, descriptor)`|Una captura de [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Una captura de la instrucción `delete`.|  
|`enumerate: function(target)`|Una captura de la [for.. en](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instrucción, [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) función, y [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Una captura de todas [captador](../../javascript/creating-objects-javascript.md) propiedades.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Una captura de [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Una captura de [Object.getPrototypeOf (función)](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Una captura de la `in` (operador), [hasOwnProperty (método) (objeto)](../../javascript/reference/hasownproperty-method-object-javascript.md)y otros métodos.|  
|`isExtensible: function(target)`|Una captura de [Object.isExtensible (función)](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Una captura de [Object.getOwnPropertyNames (función)](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Una captura de [Object.preventExtensions (función)](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Una captura de todas [establecedor](../../javascript/creating-objects-javascript.md) propiedades.|  
|`setPrototypeOf: function(target, prototype)`|Una captura de [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear un proxy para un literal de objeto mediante la captura de `get`.  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear un proxy para una función mediante la captura de `apply`.  
  
```JavaScript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
