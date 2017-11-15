---
title: Propiedades de datos y propiedades de descriptor de acceso | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="data-properties-and-accessor-properties"></a>Propiedades de datos y propiedades de descriptor de acceso
En esta sección se incluye toda la información que es probable que necesite acerca de propiedades de datos y las propiedades de descriptor de acceso.  
  
### <a name="data-properties"></a>Propiedades de datos  
 Una *propiedad datos* es una propiedad que puede obtener y establecer un valor. Las propiedades de datos contienen las propiedades `value` y `writable` en sus descriptores.  
  
 En la tabla siguiente enumeran los atributos de un descriptor de propiedad de datos.  
  
|Atributo de descriptor de datos|Descripción|Default|  
|-------------------------------|-----------------|-------------|  
|`value`|Valor actual de la propiedad.|`undefined`|  
|`writable`|`true` o `false`. Si `writable` se establece en `true`, se puede modificar el valor de propiedad.|`false`|  
|`enumerable`|`true` o `false`. Si `enumerable` se establece en `true`, la propiedad se puede enumerar mediante una instrucción `for...in`.|`false`|  
|`configurable`|`true` o `false`. Si `configurable` se establece en `true`, se pueden cambiar los atributos de la propiedad, y se puede eliminar la propiedad.|`false`|  
  
 Si el descriptor no tiene un atributo `value`, `writable`, `get` o `set` atributo y el nombre de la propiedad especificada no existe, se agrega una propiedad de datos.  
  
 Cuando el atributo `configurable` es `false` y `writable` es `true`, se pueden cambiar los atributos `value` y `writable`.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>Propiedades de datos agregadas sin usar defineProperty  
 Si se agrega una propiedad de datos sin usar las funciones `Object.defineProperty`, `Object.defineProperties` o `Object.create`, todos los atributos `writable`, `enumerable` y `configurable` se establecen en `true`. Después de que la propiedad se agrega, se puede modificar mediante la función `Object.defineProperty`.  
  
 Puede usar los siguientes métodos para agregar una propiedad de datos:  
  
-   Un operador de asignación (=), como en `obj.color = "white";`  
  
-   Un objeto literal, como en `obj = { color: "white", height: 5 };`  
  
-   Una función de construcción, como se describe en [Using Constructors to Define Types](../../javascript/advanced/using-constructors-to-define-types.md) (Uso de constructores para definir tipos)  
  
### <a name="accessor-properties"></a>Propiedades de descriptor de acceso  
 Una *propiedad de descriptor de acceso* llama a una función proporcionada por el usuario cada vez que el valor de propiedad se establece o recupera. El descriptor de una propiedad de descriptor de acceso contiene un atributo `get`, un atributo `set` o ambos.  
  
 En la tabla siguiente se enumeran los atributos de un descriptor de propiedad de descriptor de acceso.  
  
|Atributo de descriptor de descriptor de acceso|Descripción|Default|  
|-----------------------------------|-----------------|-------------|  
|`get`|Una función que devuelve el valor de propiedad. La función no tiene parámetros.|`undefined`|  
|`set`|Una función que establece el valor de propiedad. Tiene un parámetro que contiene el valor que se asigna.|`undefined`|  
|`enumerable`|`true` o `false`. Si `enumerable` se establece en `true`, la propiedad se puede enumerar mediante una instrucción `for...in`.|`false`|  
|`configurable`|`true` o `false`. Si `configurable` se establece en `true`, se pueden cambiar los atributos de la propiedad, y se puede eliminar la propiedad.|`false`|  
  
 Cuando un descriptor de acceso `get` no está definido y se realiza un intento de acceder al valor de propiedad, se devuelve el valor `undefined`. Cuando un descriptor de acceso `set` no está definido y se realiza un intento de asignar un valor a la propiedad de descriptor de acceso, no ocurre nada.  
  
### <a name="property-modifications"></a>Modificaciones de propiedades  
 Si el objeto ya tiene una propiedad con el nombre especificado, se modifican los atributos de propiedad. Cuando se modifica la propiedad, los atributos que no se especifican en el descriptor siguen siendo los mismos.  
  
 Si el atributo `configurable` de una propiedad existente es `false`, la única modificación permitida es cambiar el atributo `writable` de `true` a `false`.  
  
 Puede cambiar una propiedad de datos por una propiedad de descriptor de acceso y viceversa. Si lo hace, los atributos `configurable` y `enumerable` que no se especifican en el descriptor se conservan en la propiedad. Otros atributos que no se especifican en el descriptor se establecen en sus valores predeterminados.  
  
 Puede definir de manera incremental las propiedades de descriptor de acceso configurables con la realización de varias llamadas a la función `Object.defineProperty`. Por ejemplo, una llamada a `Object.defineProperty` podría definir únicamente un descriptor de acceso `get`. Una llamada posterior en el mismo nombre de propiedad podría definir un descriptor de acceso `set`. La propiedad tendría entonces ambos descriptores de acceso, `get` y `set`.  
  
 Para obtener un objeto de descriptor que se aplica a una propiedad existente, puede usar la función de descriptor [Object.getOwnProperty](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Puede usar la función [Object.seal](../../javascript/reference/object-seal-function-javascript.md) y la función [Object.freeze](../../javascript/reference/object-freeze-function-javascript.md) para impedir la modificación de atributos de propiedad.