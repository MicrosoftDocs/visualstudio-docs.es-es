---
title: "Object.create (Funci&#243;n de JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "create (función) [JavaScript]"
  - "Object.create (función) [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Object.create (Funci&#243;n de JavaScript)
Crea un objeto que tiene un prototipo especificado y contiene opcionalmente propiedades especificadas.  
  
## Sintaxis  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### Parámetros  
 `prototype`  
 Requerido.  Objeto que se usará como prototipo.  Puede ser un valor `null`.  
  
 `descriptors`  
 Opcional.  Objeto de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que contiene uno o varios descriptores de propiedad.  
  
 Una *propiedad de datos* es una propiedad que puede obtener y establecer un valor.  El descriptor de una propiedad de datos contiene un atributo `value`, así como atributos `writable`, `enumerable` y `configurable`.  Si los últimos tres atributos no se especifican, su valor predeterminado es `false`.  Una *propiedad de descriptor de acceso* llama a una función proporcionada por el usuario cada vez que el valor se recupera o establece.  El descriptor para una propiedad de descriptor de acceso contiene un atributo `set`, un atributo `get` o ambos.  Para obtener más información, vea [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Valor devuelto  
 Un objeto nuevo cuyo prototipo interno se ha especificado y que contiene las propiedades especificadas, si las hay.  
  
## Excepciones  
 Se produce una excepción `TypeError` si alguna de las condiciones siguientes es verdadera:  
  
-   El argumento `prototype` no es un objeto ni es `null`.  
  
-   Un descriptor del argumento `descriptors` tiene un atributo `value` o `writable` y también un atributo `get` o `set`.  
  
-   Un descriptor del argumento `descriptors` tiene un atributo `get` o `set` que no es una función.  
  
## Comentarios  
 Puede usar esta función con un parámetro `prototype` `null` para detener la cadena de prototipo.  El objeto creado no tendrá ningún prototipo.  
  
## Ejemplo  
 En el ejemplo siguiente se crea un objeto usando un prototipo `null` y se agregan dos propiedades enumerables.  
  
```javascript  
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
  
## Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene el mismo prototipo interno que el objeto Object.  Podrá ver que tiene el mismo prototipo que un objeto creado mediante un literal de objeto.  La función [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) obtiene el prototipo del objeto original.  Para obtener el descriptor de propiedad del objeto, puede usar [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```javascript  
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
  
## Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene el mismo prototipo interno que el objeto Shape.  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.getPrototypeOf \(Función\)](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf \(Método, Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Crear objetos](../../javascript/creating-objects-javascript.md)