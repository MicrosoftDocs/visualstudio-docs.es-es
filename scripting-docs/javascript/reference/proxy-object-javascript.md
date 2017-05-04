---
title: "Objeto proxy (JavaScript) | Microsoft Docs"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Objeto proxy (JavaScript)
Habilita el comportamiento personalizado de un objeto.  
  
## Sintaxis  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### Parámetros  
 `target`  
 Requerido.  Un objeto o una función que debe virtualizar el proxy.  
  
 `handler`  
 Requerido.  Un objeto con métodos \(capturas\) que implementan el comportamiento personalizado.  
  
## Comentarios  
 Se utiliza un objeto `Proxy` para interceptar las operaciones de bajo nivel internas en otro objeto.  Los objetos proxy pueden utilizarse, entre otros fines, para la intercepción, virtualización de objetos y los registros\/la generación de perfiles.  
  
 Si no se ha definido una captura para una operación determinada en el controlador para el proxy, la operación se reenvía al destino.  
  
 El objeto de controlador define los siguientes métodos \(capturas\) para implementar un comportamiento personalizado.  Los ejemplos que se muestran aquí no son exhaustivos.  Para admitir el comportamiento predeterminado condicional en el método de controlador, utilice métodos de [Objeto Reflect](../../javascript/reference/reflect-object-javascript.md).  
  
|Sintaxis de método de controlador \(captura\)|Ejemplos de uso|  
|---------------------------------------------------|---------------------|  
|`apply: function(target, thisArg, args)`|Una captura para una llamada a una función.|  
|`construct: function(target, args)`|Una captura para un constructor.|  
|`defineProperty: function(target, propertyName, descriptor)`|Una captura de [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Una captura de la instrucción `delete`.|  
|`enumerate: function(target)`|Una captura de la instrucción [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), la función [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) y [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Una captura de todas las propiedades de [captador](../../javascript/creating-objects-javascript.md).|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Una captura de [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Una captura de [Object.getPrototypeOf \(Función\)](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Una captura del operador `in`, [hasOwnProperty \(Método, Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) y otros métodos.|  
|`isExtensible: function(target)`|Una captura de [Object.isExtensible \(Función\)](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Una captura de [Object.getOwnPropertyNames \(Función\)](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Una captura de [Object.preventExtensions \(Función\)](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Una captura de todas las propiedades de [establecedor](../../javascript/creating-objects-javascript.md).|  
|`setPrototypeOf: function(target, prototype)`|Una captura de [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear un proxy para un literal de objeto mediante la captura de `get`.  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear un proxy para una función mediante la captura de `apply`.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]