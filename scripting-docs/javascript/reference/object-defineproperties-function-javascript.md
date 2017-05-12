---
title: "Object.defineProperties (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "Object.defineProperties (función) [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Object.defineProperties (Funci&#243;n de JavaScript)
Agrega una o varias propiedades a un objeto, o modifica atributos de propiedades existentes.  
  
## Sintaxis  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## Parámetros  
 `object`  
 Requerido.  Objeto en el que se van a agregar o modificar las propiedades.  Puede ser un objeto nativo de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] o un objeto DOM.  
  
 `descriptors`  
 Requerido.  Objeto de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que contiene uno o más objetos de descriptor.  Cada objeto de descriptor describe una propiedad de datos o una propiedad de descriptor de acceso.  
  
## Valor devuelto  
 Objeto que se pasó a la función.  
  
## Comentarios  
 El argumento `descriptors` es un objeto que contiene uno o más objetos de descriptor.  
  
 Una *propiedad de datos* es una propiedad que puede almacenar y recuperar un valor.  El descriptor de una propiedad de datos contiene un atributo `value`, un atributo `writable` o ambos.  Para obtener más información, vea [Propiedades de datos y propiedades del descriptor de acceso](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Una *propiedad de descriptor de acceso* llama a una función proporcionada por el usuario cada vez que se establece o se recupera el valor de propiedad.  El descriptor para una propiedad de descriptor de acceso contiene un atributo `set`, un atributo `get` o ambos.  
  
 Si el objeto ya tiene una propiedad con el nombre especificado, se modifican los atributos de la propiedad.  Para obtener más información, vea [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Para crear un objeto y agregarle propiedades, puede usar [Object.create \(Función\)](../../javascript/reference/object-create-function-javascript.md).  
  
## Agregar propiedades  
 En el ejemplo siguiente, la función `Object.defineProperties` agrega una propiedad de datos y una propiedad de descriptor de acceso a un objeto definido por el usuario.  
  
 En el ejemplo se usa un literal de objeto para crear el objeto `descriptors` con los objetos de descriptor `newDataProperty` y `newAccessorProperty`.  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Como en el ejemplo anterior, en el siguiente se agregan propiedades dinámicamente, no con un literal de objeto.  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## Modificar propiedades  
 Para modificar los atributos de propiedad del objeto, agregue el código siguiente.  La función `Object.defineProperties` modifica el atributo `writable` de `newDataProperty` y el atributo `enumerable` de `newAccessorProperty`.  Agrega `anotherDataProperty` al objeto porque el nombre de propiedad no existe todavía.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## Requisitos  
 Se admite en el modo estándar de Internet Explorer 9 y estándar de Internet Explorer 10, así como en las aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Se admite en Internet Explorer 8 para objetos DOM solamente; de lo contrario, no se admite.  
  
## Vea también  
 [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames \(Función\)](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create \(Función\)](../../javascript/reference/object-create-function-javascript.md)   
 [Object \(Objeto\)](../../javascript/reference/object-object-javascript.md)