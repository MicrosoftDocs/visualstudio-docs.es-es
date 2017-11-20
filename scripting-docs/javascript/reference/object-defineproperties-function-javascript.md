---
title: "Object.defineProperties (función) (JavaScript) | Documentos de Microsoft"
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
helpviewer_keywords: Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties (Función de JavaScript)
Agrega una o varias propiedades a un objeto y/o modifica los atributos de las propiedades existentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto en el que se va a agregar o modificar las propiedades. Esto puede ser nativo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto o un objeto DOM.  
  
 `descriptors`  
 Obligatorio. Un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto que contiene uno o varios objetos de descriptor. Cada objeto de descriptor describe una propiedad de datos o una propiedad de descriptor de acceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El objeto que se pasó a la función.  
  
## <a name="remarks"></a>Comentarios  
 El `descriptors` argumento es un objeto que contiene uno o varios objetos de descriptor.  
  
 A *propiedad datos* es una propiedad que puede almacenar y recuperar un valor. Un descriptor de propiedad de datos contiene un `value` atributo, un `writable` atributo, o ambos. Para obtener más información, consulte [propiedades de datos y las propiedades de descriptor de acceso](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Un *propiedad de descriptor de acceso* llama a una función proporcionada por el usuario cada vez que se establece o recupera el valor de propiedad. Un descriptor de propiedad de descriptor de acceso contiene un `set` atributo, un `get` atributo, o ambos.  
  
 Si el objeto ya tiene una propiedad que tiene el nombre especificado, se modifican los atributos de propiedad. Para obtener más información, consulte [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Para crear un objeto y agregar propiedades al nuevo objeto, puede usar el [Object.create (función)](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Agregar propiedades  
 En el ejemplo siguiente, la `Object.defineProperties` función agrega una propiedad de datos y una propiedad de descriptor de acceso a un objeto definido por el usuario.  
  
 En el ejemplo se usa un literal de objeto para crear el `descriptors` objeto con el `newDataProperty` y `newAccessorProperty` objetos de descriptor.  
  
```JavaScript  
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
  
 Al igual que el ejemplo anterior, en el ejemplo siguiente se agrega propiedades dinámicamente en lugar de con un literal de objeto.  
  
```JavaScript  
  
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
  
## <a name="modifying-properties"></a>Modificar propiedades  
 Para modificar los atributos de propiedad para el objeto, agregue el código siguiente. El `Object.defineProperties` función modifica el `writable` atributo de `newDataProperty`y modifica el `enumerable` atributo de `newAccessorProperty`. Agrega `anotherDataProperty` al objeto porque ese nombre de propiedad no existe ya.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Requisitos  
 Compatible con los estándares de Internet Explorer 9, Internet Explorer 10 y estándar, y [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicaciones. Se admite en Internet Explorer 8 para objetos de DOM, en caso contrario, no se admite.  
  
## <a name="see-also"></a>Vea también  
 [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames (función)](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.Create (función)](../../javascript/reference/object-create-function-javascript.md)   
 [Object (Objeto)](../../javascript/reference/object-object-javascript.md)