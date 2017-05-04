---
title: "Object.freeze (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "freeze (función)"
  - "Object.freeze (función)"
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Object.freeze (Funci&#243;n de JavaScript)
Impide la modificación de atributos y valores de propiedad existentes e impide agregar nuevas propiedades.  
  
## Sintaxis  
  
```javascript  
Object.freeze(object)  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto en el que se van a bloquear los atributos.  
  
## Valor devuelto  
 Objeto que se pasa a la función.  
  
## Excepciones  
 Si el argumento `object` no es un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
 La función `Object.freeze` hace lo siguiente:  
  
-   Hace que el objeto sea no extensible, de forma que no se le puedan agregar nuevas propiedades.  
  
-   Establece el atributo `configurable` en `false` para todas las propiedades del objeto.  Cuando `configurable` es `false`, los atributos de la propiedad no se pueden cambiar y la propiedad no se puede eliminar.  
  
-   Establece el atributo `writable` en `false` para todas las propiedades de datos del objeto.  Cuando `writable` es false, el valor de propiedad de datos no se puede cambiar.  
  
 Para obtener más información sobre cómo establecer atributos de propiedad, consulta [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).  Para obtener los atributos de una propiedad, puedes usar [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Funciones relacionadas  
 Las funciones relacionadas siguientes impiden modificar los atributos de objeto.  
  
|Función|El objeto se hace no extensible|`configurable` se establece en `false` para cada propiedad|`writable` se establece en `false` para cada propiedad|  
|-------------|-------------------------------------|----------------------------------------------------------------|------------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sí|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Sí|Sí|No|  
|`Object.freeze`|Sí|Sí|Sí|  
  
 Las siguientes funciones devuelven `true` si todas las condiciones marcadas en la tabla siguiente son verdaderas.  
  
|Función|¿Es extensible el objeto?|¿`configurable` es `false` para todas las propiedades?|¿`writable` es `false` para todas las propiedades de datos?|  
|-------------|-------------------------------|------------------------------------------------------------|-----------------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|Sí|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Object.freeze`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.preventExtensions \(Función\)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal \(Función\)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible \(Función\)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed \(Función\)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen \(Función\)](../../javascript/reference/object-isfrozen-function-javascript.md)