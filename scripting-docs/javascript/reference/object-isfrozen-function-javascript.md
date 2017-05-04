---
title: "Object.isFrozen (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "isFrozen (función) [JavaScript]"
  - "Object.isFrozen (función) [JavaScript]"
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isFrozen (Funci&#243;n de JavaScript)
Devuelve `true` si no se pueden modificar los atributos y valores de propiedad existentes en un objeto y no se pueden agregar nuevas propiedades al objeto.  
  
## Sintaxis  
  
```javascript  
Object.isFrozen(object)  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto que se va a probar.  
  
## Valor devuelto  
 Es `true` si se cumplen todas las afirmaciones siguientes:  
  
-   El objeto no es extensible, lo que indica que no se pueden agregar nuevas propiedades al objeto.  
  
-   El atributo `configurable` es `false` para todas las propiedades existentes.  
  
-   El atributo `writable` es `false` para todas las propiedades de datos existentes.  
  
 Si el objeto no tiene ninguna propiedad existente, la función devuelve `true` si el objeto no es extensible.  
  
## Excepciones  
 Si el argumento `object` no es un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
 Cuando el atributo `configurable` de una propiedad es `false`, los atributos de la propiedad no se pueden cambiar y la propiedad no se puede eliminar.  Cuando `writable` es `false`, el valor de propiedad de los datos no se puede cambiar.  Cuando `configurable` es `false` y `writable` es `true`, los atributos `value` y `writable` se pueden cambiar.  
  
 Para obtener más información sobre cómo establecer atributos de propiedad, consulta [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).  Para obtener los atributos de una propiedad, puedes usar [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Funciones relacionadas  
 Las funciones relacionadas siguientes impiden modificar los atributos de objeto.  
  
|Función|El objeto se hace no extensible|`configurable` se establece en `false` para cada propiedad|`writable` se establece en `false` para cada propiedad|  
|-------------|-------------------------------------|----------------------------------------------------------------|------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sí|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Sí|Sí|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sí|Sí|Sí|  
  
 Las siguientes funciones devuelven `true` si todas las condiciones marcadas en la tabla siguiente son verdaderas.  
  
|Función|¿Es extensible el objeto?|¿`configurable` es `false` para todas las propiedades?|¿`writable` es `false` para todas las propiedades de datos?|  
|-------------|-------------------------------|------------------------------------------------------------|-----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|`Object.isFrozen`|No|Sí|Sí|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Object.isFrozen`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.preventExtensions \(Función\)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal \(Función\)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze \(Función\)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible \(Función\)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed \(Función\)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames \(Función\)](../../javascript/reference/object-getownpropertynames-function-javascript.md)