---
title: "Object.seal (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "Object.seal (función)"
  - "seal (función)"
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.seal (Funci&#243;n de JavaScript)
Impide la modificación de atributos de propiedades existentes e impide agregar nuevas propiedades.  
  
## Sintaxis  
  
```javascript  
Object.seal(object)  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto en el que se van a bloquear los atributos.  
  
## Valor devuelto  
 Objeto que se pasa a la función.  
  
## Excepciones  
 Si el argumento `object` no es un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
 La función `Object.seal` realiza las acciones siguientes:  
  
-   Hace que el objeto sea no extensible, de forma que no se le puedan agregar nuevas propiedades.  
  
-   Establece el atributo `configurable` en `false` para todas las propiedades del objeto.  
  
 Cuando el atributo `configurable` es `false`, los atributos de la propiedad no se pueden cambiar y la propiedad no se puede eliminar.  Cuando `configurable` es `false` y `writable` es `true`, los atributos `value` y `writable` se pueden cambiar.  
  
 La función `Object.seal` no cambia el atributo `writable`.  
  
 Para obtener más información sobre cómo establecer atributos de propiedad, consulta [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).  Para obtener los atributos de una propiedad, puedes usar [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Funciones relacionadas  
 Las funciones relacionadas siguientes impiden modificar los atributos de objeto.  
  
|Función|El objeto se hace no extensible|`configurable` se establece en `false` para cada propiedad|`writable` se establece en `false` para cada propiedad|  
|-------------|-------------------------------------|----------------------------------------------------------------|------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sí|No|No|  
|`Object.seal`|Sí|Sí|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sí|Sí|Sí|  
  
 Las siguientes funciones devuelven `true` si todas las condiciones marcadas en la tabla siguiente son verdaderas.  
  
|Función|¿Es extensible el objeto?|¿`configurable` es `false` para todas las propiedades?|¿`writable` es `false` para todas las propiedades de datos?|  
|-------------|-------------------------------|------------------------------------------------------------|-----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Object.seal`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.preventExtensions \(Función\)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.freeze \(Función\)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible \(Función\)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed \(Función\)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen \(Función\)](../../javascript/reference/object-isfrozen-function-javascript.md)