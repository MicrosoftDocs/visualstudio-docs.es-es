---
title: "Propiedades de datos y propiedades del descriptor de acceso | Microsoft Docs"
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
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propiedades de datos y propiedades del descriptor de acceso
Esta sección incluye toda la información que probablemente necesitarás sobre las propiedades de datos y las propiedades de descriptor de acceso.  
  
### Propiedades de datos  
 Una *propiedad de datos* es una propiedad que puede obtener y establecer un valor.  Las propiedades de datos contienen las propiedades `value` y `writable` en sus descriptores.  
  
 En la tabla siguiente se enumeran los atributos para un descriptor de una propiedad de datos.  
  
|Atributo de descriptor de datos|Descripción|Default|  
|-------------------------------------|-----------------|-------------|  
|`value`|Valor actual de la propiedad.|`undefined`|  
|`writable`|`true` o `false`.  Si `writable` se establece en `true`, se puede modificar el valor de propiedad.|`false`|  
|`enumerable`|`true` o `false`.  Si `enumerable` se establece en `true`, una instrucción `for…in` puede enumerar la propiedad.|`false`|  
|`configurable`|`true` o `false`.  Si `configurable` se establece en `true`, se pueden cambiar los atributos de propiedad y se puede eliminar la propiedad.|`false`|  
  
 Si descriptor no tiene un atributo `value`, `writable`, `get` o `set` y no existe el nombre de propiedad especificado, se agrega una propiedad de datos.  
  
 Cuando el atributo `configurable` es `false` y `writable` es `true`, se pueden cambiar los atributos `value` y `writable`.  
  
#### Propiedades de datos agregadas sin usar defineProperty  
 Si agregas una propiedad de datos sin usar las funciones `Object.defineProperty`, `Object.defineProperties` o `Object.create`, los atributos `writable`, `enumerable` y `configurable` se establecen en `true`.  Una vez agregada la propiedad, puedes modificarla mediante la función `Object.defineProperty`.  
  
 Puedes usar lo siguiente para agregar una propiedad de datos:  
  
-   Un operador de asignación \(\=\), como en `obj.color = "white";`  
  
-   Un literal de objeto, como en `obj = { color: "white", height: 5 };`  
  
-   Una función de construcción, como se describe en [Utilizar constructores para definir tipos](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### Propiedades de descriptor de acceso  
 Una *propiedad de descriptor de acceso* llama a una función proporcionada por el usuario cada vez que se establece o se recupera el valor de propiedad.  El descriptor para una propiedad de descriptor de acceso contiene un atributo `get`, un atributo `set` o ambos.  
  
 En la tabla siguiente se enumeran los atributos para un descriptor de una propiedad de descriptor de acceso.  
  
|Atributo de descriptor de acceso|Descripción|Default|  
|--------------------------------------|-----------------|-------------|  
|`get`|Función que devuelve el valor de propiedad.  La función no tiene parámetros.|`undefined`|  
|`set`|Función que establece el valor de propiedad.  Tiene un parámetro que contiene el valor que se va a asignar.|`undefined`|  
|`enumerable`|`true` o `false`.  Si `enumerable` se establece en `true`, una instrucción `for…in` puede enumerar la propiedad.|`false`|  
|`configurable`|`true` o `false`.  Si `configurable` se establece en `true`, se pueden cambiar los atributos de propiedad y se puede eliminar la propiedad.|`false`|  
  
 Cuando un descriptor de acceso `get` es indefinido y se intenta tener acceso al valor de propiedad, se devuelve el valor `undefined`.  Cuando un descriptor de acceso `set` es indefinido y se intenta asignar un valor a la propiedad de descriptor de acceso, no ocurre nada.  
  
### Modificaciones de propiedades  
 Si el objeto ya tiene una propiedad con el nombre especificado, se modifican los atributos de la propiedad.  Cuando modificas la propiedad, los atributos que no se especifican en el descriptor siguen siendo iguales.  
  
 Si el atributo `configurable` de una propiedad existente es `false`, la única modificación permitida consiste en cambiar el atributo `writable` de `true` a `false`.  
  
 Puedes cambiar una propiedad de datos a una propiedad de descriptor de acceso y viceversa.  Si lo haces, los atributos `configurable` y `enumerable` que no se especifican en el descriptor se mantienen en la propiedad.  Otros atributos que no se especifican en el descriptor se establecen en sus valores predeterminados.  
  
 Puedes definir incrementalmente propiedades configurables de descriptor de acceso usando varias llamadas a la función `Object.defineProperty`.  Por ejemplo, una llamada a `Object.defineProperty` podría definir únicamente un descriptor de acceso `get`.  Una llamada posterior en el mismo nombre de propiedad podría definir un descriptor de acceso `set`.  La propiedad tendría entonces los descriptores de acceso `get` y `set`.  
  
 Para obtener un objeto de descriptor que se aplica a una propiedad existente, puedes usar [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Puedes usar [Object.seal \(Función\)](../../javascript/reference/object-seal-function-javascript.md) y [Object.freeze \(Función\)](../../javascript/reference/object-freeze-function-javascript.md) para impedir la modificación de los atributos de propiedad.