---
title: "Object.getOwnPropertyDescriptor (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Object.getOwnPropertyDescriptor (Función de JavaScript)
Obtiene el descriptor de propiedad propia del objeto especificado. Un descriptor de propiedad propia es aquel que se define directamente en el objeto y no se hereda del prototipo del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. El objeto que contiene la propiedad.  
  
 `propertyname`  
 Obligatorio. Nombre de la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Descriptor de la propiedad.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar la función `Object.getOwnPropertyDescriptor` para obtener un objeto de descriptor que describa los atributos de la propiedad.  
  
 El [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md) se utiliza para agregar o modificar las propiedades.  
  
## <a name="data-property-example"></a>Ejemplo de propiedad de datos  
 En el ejemplo siguiente se obtiene un descriptor de propiedad de datos y se usa para hacer que la propiedad sea de solo lectura.  
  
```JavaScript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Para obtener una lista de los atributos de propiedad, puede agregar el código siguiente a este ejemplo.  
  
```JavaScript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## <a name="requirements"></a>Requisitos  
 Se admiten todas las características en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] admite objetos DOM, pero no objetos definidos por el usuario. Se pueden especificar los atributos `enumerable` y `configurable` , aunque no se usan.  
  
## <a name="see-also"></a>Vea también  
 [Prototipos de modelo de objetos de documento, parte 2: Descriptor de acceso (captador/establecedor) soporte técnico](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty (Función)](../../javascript/reference/object-defineproperty-function-javascript.md)