---
title: "Crear objetos (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "funciones constructoras"
  - "constructores, incluir propiedades y métodos"
  - "crear objetos"
  - "crear objetos, acerca de crear objetos"
  - "crear objetos, funciones constructoras"
  - "crear objetos, prototipos"
  - "objetos personalizados"
  - "objetos personalizados, crear"
  - "Function (constructor)"
  - "inicializar objetos, utilizar constructores"
  - "objetos, crear [JavaScript]"
  - "objetos prototipo"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Crear objetos (JavaScript)
Dispone de varias maneras de crear sus propios objetos en JavaScript.  Puede crear directamente instancias de un [Object \(Objeto\)](../javascript/reference/object-object-javascript.md) y, después, agregar sus propios métodos y propiedades.  También puede usar la notación literal de objeto para definirlo.  Igualmente, puede usar una función constructora para definir un objeto.  Si quiere más información sobre el uso de funciones constructoras, vea [Utilizar constructores para definir tipos](../javascript/advanced/using-constructors-to-define-types.md).  
  
## Ejemplo  
 El código siguiente muestra cómo crear una instancia de un objeto y agregar algunas propiedades.  En este caso, solo el objeto `pasta` tiene las propiedades `grain`, `width` y `shape`.  
  
```javascript  
var pasta = new Object();  
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
  
## Literales de objeto  
 También puede usar la notación literal de objeto para crear una única instancia de un objeto.  El código siguiente muestra cómo crear una instancia de un objeto usando la notación literal de objeto.  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 También puede usar un literal de objeto dentro de un constructor.  
  
> [!CAUTION]
>  Las siguientes características solo se admiten en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 En [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)], puede usar la sintaxis abreviada para crear un literal de objeto.  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 En el ejemplo siguiente se muestra el uso de la sintaxis abreviada para definir métodos en literales de objeto.  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 También puede establecer los nombres de propiedad dinámicamente en literales de objeto en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  En el ejemplo de código siguiente se crea un nombre de propiedad para un objeto dinámicamente mediante la sintaxis Set.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
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
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 En el ejemplo de código siguiente se crea una propiedad calculada mediante la [sintaxis de la función de flecha](../javascript/functions-javascript.md) para anexar 42 al nombre de propiedad.  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```