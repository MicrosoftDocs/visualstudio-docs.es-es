---
title: "Object.Freeze (función) (JavaScript) | Documentos de Microsoft"
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze (Función de JavaScript)
Evita la modificación de valores y atributos de propiedad existentes y evita la adición de propiedades nuevas.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto en el que se va a bloquear los atributos.  
  
## <a name="return-value"></a>Valor devuelto  
 El objeto que se pasa a la función.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 El `Object.freeze` función hace lo siguiente:  
  
-   Hace que el objeto no es extensible, por lo que no se pueden agregar propiedades nuevas a él.  
  
-   Establece el `configurable` atribuir a `false` para todas las propiedades del objeto. Cuando `configurable` es `false`, no se puede cambiar los atributos de propiedad y no se puede eliminar la propiedad.  
  
-   Establece el `writable` atribuir a `false` para todas las propiedades de datos del objeto. Cuando `writable` es false, no se puede cambiar el valor de propiedad de datos.  
  
 Para obtener más información sobre cómo establecer atributos de propiedad, vea [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md). Para obtener los atributos de una propiedad, puede usar el [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funciones relacionadas  
 Las siguientes funciones relacionadas evitar la modificación de atributos de objetos.  
  
|Función|Objeto estará no extensible|`configurable`se establece en `false` para cada propiedad|`writable`se establece en `false` para cada propiedad|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sí|No|No|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Sí|Sí|No|  
|`Object.freeze`|Sí|Sí|Sí|  
  
 Las funciones siguientes devuelven `true` si se cumplen todas las condiciones que se marcan en la tabla siguiente.  
  
|Función|¿Objeto es extensible?|`configurable`¿es `false` para todas las propiedades?|`writable`¿es `false` para todas las propiedades de datos?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|Sí|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.freeze`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.preventExtensions (función)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal (función)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible (función)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed (función)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen (Función)](../../javascript/reference/object-isfrozen-function-javascript.md)