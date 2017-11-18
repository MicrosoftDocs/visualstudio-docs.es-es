---
title: "Object.defineProperty (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty (Función de JavaScript)
Agrega una propiedad a un objeto o modifica los atributos de una propiedad existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto en el que se va a agregar o modificar la propiedad. Puede ser un objeto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nativo (es decir, un objeto definido por el usuario o un objeto integrado) o un objeto DOM.  
  
 `propertyname`  
 Obligatorio. Cadena que contiene el nombre de la propiedad.  
  
 `descriptor`  
 Obligatorio. Descriptor de la propiedad. Puede ser para una propiedad de datos o una propiedad de descriptor de acceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Objeto modificado.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar la función `Object.defineProperty` para hacer lo siguiente:  
  
-   Agregar una nueva propiedad a un objeto. Esto sucede cuando el objeto no tiene el nombre de propiedad especificado.  
  
-   Modificar los atributos de una propiedad existente. Esto sucede cuando el objeto ya tiene el nombre de propiedad especificado.  
  
 La definición de propiedad se proporciona en un objeto de descriptor que describe los atributos de una propiedad de datos o una propiedad de descriptor de acceso. El objeto de descriptor es un parámetro de la función `Object.defineProperty`.  
  
 Para agregar varias propiedades a un objeto, o para modificar varias propiedades existentes, puede usar el [Object.defineProperties (función)](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## <a name="exceptions"></a>Excepciones  
 Se produce una excepción `TypeError` si alguna de las condiciones siguientes es true:  
  
-   El argumento `object` no es un objeto.  
  
-   El objeto no es [extensible](../../javascript/reference/object-isextensible-function-javascript.md) y el nombre de propiedad especificado no existe...  
  
-   `descriptor` tiene un atributo `value` o `writable` y un atributo `get` o `set`.  
  
-   `descriptor` tiene un atributo `get` o `set` que no es una función o no está definido.  
  
-   El nombre de propiedad especificado ya existe, la propiedad existente tiene un atributo `configurable` de `false`, y `descriptor` contiene uno o más atributos que son diferentes de los de la propiedad existente. Sin embargo, cuando la propiedad existente tiene un atributo `configurable` de `false` y un atributo `writable` de `true`, se permite que el atributo `value` o `writable` sea diferente.  
  
## <a name="adding-a-data-property"></a>Agregar una propiedad de datos  
 En el ejemplo siguiente, la función `Object.defineProperty` agrega una propiedad de datos a un objeto definido por el usuario. Para agregar en su lugar la propiedad a un objeto DOM existente, quite los comentarios de la línea `var = window.document`.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Para obtener una lista de las propiedades del objeto, agregue el código siguiente a este ejemplo.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>Modificar una propiedad de datos  
 Para modificar un atributo de propiedad para el objeto, agregue el código siguiente a la función `addDataProperty` mostrada anteriormente. El parámetro `descriptor` solo contiene un atributo `writable`. Los demás atributos de la propiedad de datos siguen siendo los mismos.  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>Agregar una propiedad de descriptor de acceso  
 En el ejemplo siguiente, la función `Object.defineProperty` agrega una propiedad de descriptor de acceso a un objeto definido por el usuario.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Para obtener una lista de las propiedades del objeto, agregue el código siguiente a este ejemplo.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>Modificar una propiedad de descriptor de acceso  
 Para modificar un atributo de propiedad para el objeto, agregue el código siguiente al código mostrado anteriormente. El parámetro `descriptor` solo contiene una definición de descriptor de acceso `get`. Los demás atributos de la propiedad siguen siendo los mismos.  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>Modificar una propiedad de un elemento DOM  
 En el ejemplo siguiente se muestra cómo personalizar las propiedades integradas de DOM mediante la función `Object.getOwnPropertyDescriptor` para obtener y modificar el descriptor de la propiedad. En este ejemplo, debe haber un elemento DIV con el identificador "div".  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>Requisitos  
 El modo estándar de Internet Explorer 9 y el modo estándar de Internet Explorer 10, así como las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], admiten todas las características.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] admite objetos DOM, pero no objetos definidos por el usuario. Se pueden especificar los atributos `enumerable` y `configurable` , aunque no se usan.  
  
## <a name="see-also"></a>Vea también  
 [Prototipos de modelo de objetos de documento, parte 2: Descriptor de acceso (captador/establecedor) soporte técnico](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperties (función)](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.Create (función)](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames (Función)](../../javascript/reference/object-getownpropertynames-function-javascript.md)