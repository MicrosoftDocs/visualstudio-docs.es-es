---
title: Object.Keys (función) (JavaScript) | Documentos de Microsoft
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639755"
---
# <a name="objectkeys-function-javascript"></a>Object.keys (Función de JavaScript)
Devuelve los nombres de las propiedades y métodos enumerables de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`object`|Obligatorio. El objeto que contiene las propiedades y métodos. Puede tratarse de un objeto que ha creado o un objeto existente de Document Object Model (DOM).|  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz que contiene los nombres de las propiedades y métodos del objeto.  
  
## <a name="exceptions"></a>Excepciones  
 Si el valor proporcionado para el `object` argumento no es el nombre de un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 El `keys` método devuelve solo los nombres de propiedades y métodos. Para devolver los nombres de métodos y propiedades enumerables y no es enumerable, puede utilizar [Object.getOwnPropertyNames (función)](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Para obtener información sobre la `enumerable` atributos de una propiedad, vea [Object.defineProperty (función)](../../javascript/reference/object-defineproperty-function-javascript.md) y [Object.getOwnPropertyDescriptor (función)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene tres propiedades y un método. A continuación, utiliza el `keys` método para obtener las propiedades y métodos del objeto.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente muestra los nombres de todas las propiedades que comienzan con la letra "g" en el objeto de Pasta.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.getOwnPropertyNames (Función)](../../javascript/reference/object-getownpropertynames-function-javascript.md)