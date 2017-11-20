---
title: "Object.isFrozen (función) (JavaScript) | Documentos de Microsoft"
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
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectisfrozen-function-javascript"></a>Object.isFrozen (Función de JavaScript)
Devuelve `true` si no se puede modificar los atributos de propiedad y valores existentes en un objeto y no se pueden agregar propiedades nuevas al objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si se cumplen todas de las acciones siguientes:  
  
-   El objeto es no es extensible, lo que indica que no se pueden agregar propiedades nuevas al objeto.  
  
-   El `configurable` atributo es `false` para todas las propiedades existentes.  
  
-   El `writable` atributo es `false` para todas las propiedades de datos existente.  
  
 Si el objeto no tiene ninguna propiedad existente, la función devuelve `true` si el objeto es no extensible.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el `configurable` atributo de una propiedad es `false`, no se puede cambiar los atributos de propiedad y no se puede eliminar la propiedad. Cuando `writable` es `false`, no se puede cambiar el valor de propiedad de datos. Cuando `configurable` es `false` y `writable` es `true`, `value` y `writable` atributos se pueden cambiar.  
  
 Para obtener información sobre cómo establecer atributos de propiedad, vea [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md). Para obtener los atributos de una propiedad, puede usar el [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funciones relacionadas  
 Las siguientes funciones relacionadas evitar la modificación de atributos de objetos.  
  
|Función|Objeto estará no extensible|`configurable`se establece en `false` para cada propiedad|`writable`se establece en `false` para cada propiedad|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sí|No|No|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Sí|Sí|No|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sí|Sí|Sí|  
  
 Las funciones siguientes devuelven `true` si se cumplen todas las condiciones que se marcan en la tabla siguiente.  
  
|Función|¿Objeto es extensible?|`configurable`¿es `false` para todas las propiedades?|`writable`¿es `false` para todas las propiedades de datos?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|`Object.isFrozen`|No|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.isFrozen`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.preventExtensions (función)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal (función)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze (función)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible (función)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed (función)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames (Función)](../../javascript/reference/object-getownpropertynames-function-javascript.md)