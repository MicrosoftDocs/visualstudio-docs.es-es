---
title: "Object.isExtensible (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "isExtensible (función) [JavaScript]"
  - "Object.isExtensible (función) [JavaScript]"
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isExtensible (Funci&#243;n de JavaScript)
Devuelve un valor que indica si se pueden agregar nuevas propiedades a un objeto.  
  
## Sintaxis  
  
```javascript  
Object.isExtensible(object)  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto que se va a probar.  
  
## Valor devuelto  
 `true` si el objeto es extensible, lo que indica que se pueden agregar nuevas propiedades al objeto; de lo contrario, `false`.  
  
## Excepciones  
 Si el argumento `object` no es un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
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
|`Object.isExtensible`|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Object.isExtensible`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.preventExtensions \(Función\)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal \(Función\)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze \(Función\)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed \(Función\)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen \(Función\)](../../javascript/reference/object-isfrozen-function-javascript.md)