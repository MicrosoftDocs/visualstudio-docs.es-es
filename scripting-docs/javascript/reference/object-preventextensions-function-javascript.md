---
title: "Object.preventExtensions (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions (función) [JavaScript]"
  - "preventExtensions (función) [JavaScript]"
  - "impedir propiedades nuevas [JavaScript]"
  - "propiedades [JavaScript], impedir nuevas"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.preventExtensions (Funci&#243;n de JavaScript)
Impide la adición de nuevas propiedades a un objeto.  
  
## Sintaxis  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto que se va a hacer no extensible.  
  
## Valor devuelto  
 Objeto que se pasa a la función.  
  
## Excepciones  
 Si el argumento `object` no es un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
 La función `Object.preventExtensions` hace que un objeto sea no extensible, por lo que no se le pueden agregar nuevas propiedades con nombre.  Después de hacer que un objeto sea no extensible, no puede hacerse extensible.  
  
 Para obtener más información sobre cómo establecer atributos de propiedad, consulta [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Funciones relacionadas  
 Las funciones relacionadas siguientes impiden modificar los atributos de objeto.  
  
|Función|El objeto se hace no extensible|`configurable` se establece en `false` para cada propiedad|`writable` se establece en `false` para cada propiedad|  
|-------------|-------------------------------------|----------------------------------------------------------------|------------------------------------------------------------|  
|`Object.preventExtensions`|Sí|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Sí|Sí|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sí|Sí|Sí|  
  
 Las siguientes funciones devuelven `true` si todas las condiciones marcadas en la tabla siguiente son verdaderas.  
  
|Función|¿Es extensible el objeto?|¿`configurable` es `false` para todas las propiedades?|¿`writable` es `false` para todas las propiedades de datos?|  
|-------------|-------------------------------|------------------------------------------------------------|-----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Object.preventExtensions`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.seal \(Función\)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze \(Función\)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible \(Función\)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed \(Función\)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen \(Función\)](../../javascript/reference/object-isfrozen-function-javascript.md)