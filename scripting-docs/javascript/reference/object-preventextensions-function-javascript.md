---
title: "Object.preventExtensions (función) (JavaScript) | Documentos de Microsoft"
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
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectpreventextensions-function-javascript"></a>Object.preventExtensions (Función de JavaScript)
Evita la adición de propiedades nuevas a un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. El objeto que se va a hacer no extensible.  
  
## <a name="return-value"></a>Valor devuelto  
 El objeto que se pasa a la función.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 El `Object.preventExtensions` función hace que un objeto no es extensible, por lo que no se puede agregar nuevas propiedades con nombre. Después de realiza un objeto no extensible, no se puede establecer extensible.  
  
 Para obtener información sobre cómo establecer atributos de propiedad, vea [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="related-functions"></a>Funciones relacionadas  
 Las siguientes funciones relacionadas evitar la modificación de atributos de objetos.  
  
|Función|Objeto estará no extensible|`configurable`se establece en `false` para cada propiedad|`writable`se establece en `false` para cada propiedad|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|Sí|No|No|  
|[Object.Seal](../../javascript/reference/object-seal-function-javascript.md)|Sí|Sí|No|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sí|Sí|Sí|  
  
 Las funciones siguientes devuelven `true` si se cumplen todas las condiciones que se marcan en la tabla siguiente.  
  
|Función|¿Objeto es extensible?|`configurable`¿es `false` para todas las propiedades?|`writable`¿es `false` para todas las propiedades de datos?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.preventExtensions`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.Seal (función)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze (función)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible (función)](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed (función)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen (Función)](../../javascript/reference/object-isfrozen-function-javascript.md)