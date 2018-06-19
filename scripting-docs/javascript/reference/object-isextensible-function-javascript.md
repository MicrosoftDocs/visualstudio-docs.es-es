---
title: Object.isExtensible (función) (JavaScript) | Documentos de Microsoft
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
- Object.isExtensible function [JavaScript]
- isExtensible function [JavaScript]
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f88a61917811a5c6b5583e6c30539efc682296df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641105"
---
# <a name="objectisextensible-function-javascript"></a>Object.isExtensible (Función de JavaScript)
Devuelve un valor que indica si se pueden agregar propiedades nuevas a un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.isExtensible(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si el objeto es extensible, lo que indica que se pueden agregar nuevas propiedades para el objeto; en caso contrario, `false`.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
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
|`Object.isExtensible`|Sí|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sí|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.isExtensible`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.preventExtensions (función)](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal (función)](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.Freeze (función)](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed (función)](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen (Función)](../../javascript/reference/object-isfrozen-function-javascript.md)