---
title: Object.Seal (función) (JavaScript) | Documentos de Microsoft
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641155"
---
# <a name="objectseal-function-javascript"></a>Object.seal (Función de JavaScript)
Evita la modificación de atributos de las propiedades existentes y evita la adición de propiedades nuevas.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto en el que se va a bloquear los atributos.  
  
## <a name="return-value"></a>Valor devuelto  
 El objeto que se pasa a la función.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 El `Object.seal` hace función las dos acciones siguientes:  
  
-   Hace que el objeto no es extensible, por lo que no se pueden agregar propiedades nuevas a él.  
  
-   Establece el `configurable` atribuir a `false` para todas las propiedades del objeto.  
  
 Cuando el `configurable` atributo es `false`, no se puede cambiar los atributos de propiedad y no se puede eliminar la propiedad. Cuando `configurable` es `false` y `writable` es `true`, `value` y `writable` atributos se pueden cambiar.  
  
 El `Object.seal` función no cambia el `writable` atributo.  
  
 Para obtener más información sobre cómo establecer atributos de propiedad, vea [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md). Para obtener los atributos de una propiedad, puede usar el [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funciones relacionadas  
 Las siguientes funciones relacionadas evitar la modificación de atributos de objetos.  
  
|Función|Objeto estará no extensible|`configurable`se establece en `false` para cada propiedad|`writable`se establece en `false` para cada propiedad|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sí|No|No|  
|`Object.seal`|Sí|Sí|No|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sí|Sí|Sí|  
  
 Las funciones siguientes devuelven `true` si se cumplen todas las condiciones que se marcan en la tabla siguiente.  
  
|Función|¿Objeto es extensible?|`configurable`¿es `false` para todas las propiedades?|`writable`¿es `false` para todas las propiedades de datos?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.seal`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Object.Freeze (función)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible (función)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed (función)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen (Función)](../../javascript/reference/object-isfrozen-function-javascript.md)