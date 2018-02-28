---
title: Objeto Object (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- object
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Object object
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e82b9c66c286c7f847e7b67b1b5928aadd613e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="object-object-javascript"></a>Object (Objeto de JavaScript)
Ofrece funciones comunes para todos los objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
obj  
 = new Object([value])   
```  
  
## <a name="parameters"></a>Parámetros  
 `obj`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Object`.  
  
 *value*  
 Opcional. Uno de los tipos de datos primitivos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] (Number, Boolean o String). Si el valor es un objeto, el objeto se devuelve sin modificar. Si *valor* es `null`, **indefinido**, o no se proporciona, se crea un objeto sin contenido.  
  
## <a name="remarks"></a>Comentarios  
 El objeto `Object` está incluido en todos los demás objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]; todos sus métodos y propiedades están disponibles en todos los demás objetos. Los métodos pueden redefinirse en objetos definidos por el usuario y [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] los llama en los momentos adecuados. El **toString** método es un ejemplo de frecuentemente redefinido `Object` método.  
  
 En esta referencia del lenguaje, la descripción de cada método `Object` incluye información de implementación predeterminada y específica del objeto para los objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrínsecos.  
  
## <a name="requirements"></a>Requisitos  
 `Object Object` se presentó por primera vez en [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)]. Algunos miembros de las listas siguientes se presentaron en versiones posteriores.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades de `Object Object`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[__proto\_ \_ propiedad](../../javascript/reference/proto-property-object-javascript.md)|Especifica el prototipo de un objeto.|  
|[constructor (Propiedad)](../../javascript/reference/constructor-property-object-javascript.md)|Especifica la función que crea un objeto.|  
|[prototype (Propiedad)](../../javascript/reference/prototype-property-object-javascript.md)|Devuelve una referencia al prototipo correspondiente a una clase de objetos.|  
  
## <a name="functions"></a>Funciones  
 En la tabla siguiente se muestran las funciones de `Object Object`.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[Object.assign (función)](../../javascript/reference/object-assign-function-object-javascript.md)|Copia los valores de uno o varios objetos de origen en un objeto de destino.|  
|[Object.create (Función)](../../javascript/reference/object-create-function-javascript.md)|Crea un objeto que tiene un prototipo especificado y que opcionalmente contiene las propiedades especificadas.|  
|[Object.defineProperties (Función)](../../javascript/reference/object-defineproperties-function-javascript.md)|Agrega una o varias propiedades a un objeto y/o modifica los atributos de las propiedades existentes.|  
|[Object.defineProperty (Función)](../../javascript/reference/object-defineproperty-function-javascript.md)|Agrega una propiedad a un objeto o modifica los atributos de una propiedad existente.|  
|[Object.freeze (Función)](../../javascript/reference/object-freeze-function-javascript.md)|Evita la modificación de valores y atributos de propiedad existentes y evita la adición de propiedades nuevas.|  
|[Object.getOwnPropertyDescriptor (Función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Devuelve la definición de una propiedad de datos o una propiedad de descriptor de acceso.|  
|[Object.getOwnPropertyNames (Función)](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Devuelve los nombres de las propiedades y métodos de un objeto.|  
|[Object.getOwnPropertySymbols (Función)](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Devuelve las propiedades de símbolos de un objeto.|  
|[Object.getPrototypeOf (Función)](../../javascript/reference/object-getprototypeof-function-javascript.md)|Devuelve el prototipo de un objeto.|  
|[Object.is (Función)](../../javascript/reference/object-is-function-javascript.md)|Devuelve un valor que indica si dos valores son el mismo valor.|  
|[Object.isExtensible (Función)](../../javascript/reference/object-isextensible-function-javascript.md)|Devuelve un valor que indica si se pueden agregar propiedades nuevas a un objeto.|  
|[Object.isFrozen (Función)](../../javascript/reference/object-isfrozen-function-javascript.md)|Devuelve `true` si no se pueden modificar los valores y atributos de propiedad existentes de un objeto y si no se pueden agregar propiedades nuevas al objeto.|  
|[Object.isSealed (Función)](../../javascript/reference/object-issealed-function-javascript.md)|Devuelve `true` si no se pueden modificar los atributos de propiedad existentes de un objeto y si no se pueden agregar propiedades nuevas al objeto.|  
|[Object.keys (Función)](../../javascript/reference/object-keys-function-javascript.md)|Devuelve los nombres de las propiedades y métodos enumerables de un objeto.|  
|[Object.preventExtensions (Función)](../../javascript/reference/object-preventextensions-function-javascript.md)|Evita la adición de propiedades nuevas a un objeto.|  
|[Object.seal (Función)](../../javascript/reference/object-seal-function-javascript.md)|Evita la modificación de atributos de las propiedades existentes y evita la adición de propiedades nuevas.|  
|[Object.setPrototypeOf (Función)](../../javascript/reference/object-setprototypeof-function-javascript.md)|Establece el prototipo de un objeto.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos de `Object Object`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[hasOwnProperty (método)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[isPrototypeOf (método)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la jerarquía de prototipo de otro objeto.|  
|[propertyIsEnumerable (método)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[toLocaleString (método)](../../javascript/reference/tolocalestring-method-object-javascript.md)|Devuelve un objeto convertido en una cadena según la configuración regional actual.|  
|[toString (método)](../../javascript/reference/tostring-method-object-javascript.md)|Devuelve una representación de cadena de un objeto.|  
|[valueOf (método)](../../javascript/reference/valueof-method-object-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## <a name="see-also"></a>Vea también  
 [Objetos de JavaScript](../../javascript/reference/javascript-objects.md)