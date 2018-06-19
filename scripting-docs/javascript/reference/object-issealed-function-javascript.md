---
title: Object.isSealed (función) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642005"
---
# <a name="objectissealed-function-javascript"></a>Object.isSealed (Función de JavaScript)
Devuelve `true` si no se pueden modificar los atributos de propiedad existentes de un objeto y si no se pueden agregar propiedades nuevas al objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si se cumplen dos de las siguientes acciones:  
  
-   El objeto es no es extensible, lo que indica que no se pueden agregar propiedades nuevas al objeto.  
  
-   El `configurable` atributo es `false` para todas las propiedades existentes.  
  
 Si el objeto no tiene ninguna propiedad, la función devuelve `true` si el objeto es no extensible.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el `configurable` atributo de una propiedad es `false`, no se puede cambiar los atributos de propiedad y no se puede eliminar la propiedad. Cuando `writable` es `false`, no se puede cambiar el valor de propiedad de datos. Cuando `configurable` es `false` y `writable` es `true`, `value` y `writable` atributos se pueden cambiar.  
  
 El `Object.isSealed` función no usa el `writable` atributos de propiedades para determinar su valor devuelto.  
  
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
|`Object.isSealed`|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.isSealed`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.preventExtensions (función)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal (función)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze (función)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible (función)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen (función)](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor (Función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)