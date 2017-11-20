---
title: "Object.getOwnPropertyNames (función) (JavaScript) | Documentos de Microsoft"
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames (Función de JavaScript)
Devuelve los nombres de las propiedades de un objeto propios. Las propiedades de un objeto propias son aquellos que se definen directamente en ese objeto y no se heredan del prototipo del objeto. Las propiedades de un objeto incluyen campos (objetos) y funciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`object`|Obligatorio. El objeto que contiene las propiedades del propias.|  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz que contiene los nombres de las propiedades del objeto propios.  
  
## <a name="exceptions"></a>Excepciones  
 Si el valor proporcionado para el `object` argumento no es el nombre de un objeto, un `TypeError` se produce la excepción.  
  
## <a name="remarks"></a>Comentarios  
 El `getOwnPropertyNames` método devuelve los nombres de métodos y propiedades enumerables y no es enumerable. Para devolver sólo los nombres de propiedades y métodos, puede usar el [Object.keys (función)](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene tres propiedades y un método. A continuación, utiliza el `getOwnPropertyNames` método para obtener las propiedades del propias (incluido el método) del objeto.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los nombres de propiedades que comienzan con la letra ' en un **spaghetti** objeto se construyó con el **Pasta** constructor.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object.keys (Función)](../../javascript/reference/object-keys-function-javascript.md)