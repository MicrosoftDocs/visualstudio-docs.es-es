---
title: Creación de objetos (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569205"
---
# <a name="creating-objects-javascript"></a>Crear objetos (JavaScript)
Dispone de varias maneras de crear sus propios objetos en JavaScript. Puede crear directamente instancias de un [objeto](../javascript/reference/object-object-javascript.md) y luego agregar sus propias propiedades y métodos. También puede usar la notación literal de objeto para definirlo. Igualmente, puede usar una función constructora para definir un objeto. Para obtener más información sobre el uso de funciones de constructor, consulte [Using Constructors to Define Types](../javascript/advanced/using-constructors-to-define-types.md) (Uso de constructores para definir tipos).  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo crear una instancia de un objeto y agregar algunas propiedades. En este caso, solo el objeto `pasta` tiene las propiedades `grain`, `width` y `shape`.  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>Literales de objeto  
 También puede usar la notación literal de objeto para crear una única instancia de un objeto. El código siguiente muestra cómo crear una instancia de un objeto usando la notación literal de objeto.  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 También puede usar un literal de objeto dentro de un constructor.  
  
> [!CAUTION]
>  Las siguientes características solo se admiten en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 En [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)], puede usar la sintaxis abreviada para crear un literal de objeto.  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 En el ejemplo siguiente se muestra el uso de la sintaxis abreviada para definir métodos en literales de objeto.  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 También puede establecer los nombres de propiedad dinámicamente en literales de objeto en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)]. En el ejemplo de código siguiente se crea un nombre de propiedad para un objeto dinámicamente mediante la sintaxis Set.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 En el ejemplo de código siguiente se crea un nombre de propiedad para un objeto dinámicamente mediante la sintaxis Get.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 En el ejemplo de código siguiente se crea una propiedad calculada mediante la [sintaxis de la función de flecha](../javascript/functions-javascript.md) para anexar 42 al nombre de propiedad.  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```
