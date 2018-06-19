---
title: Object.getPrototypeOf (función) (JavaScript) | Documentos de Microsoft
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
- getPrototypeOf function [JavaScript]
- Object.getPrototypeOf function [JavaScript]
ms.assetid: 1c59cd7a-a7e2-4c5c-83ec-e6bd2b104d9f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c752c57fcc47192bb43790b2e93dd74fcdfbb65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638815"
---
# <a name="objectgetprototypeof-function-javascript"></a>Object.getPrototypeOf (Función de JavaScript)
Devuelve el prototipo de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
Object.getPrototypeOf(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. El objeto que hace referencia el prototipo.  
  
## <a name="return-value"></a>Valor devuelto  
 El prototipo de la `object` argumento. El prototipo también es un objeto.  
  
## <a name="exceptions"></a>Excepciones  
 Si el `object` argumento no es un objeto, un `TypeError` se produce la excepción.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Object.getPrototypeOf`.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width) {  
    this.grain = grain;  
    this.width = width;  
}  
// Create an object from the pasta constructor.  
var spaghetti = new Pasta("wheat", 0.2);  
  
// Obtain the prototype from the object.  
var proto = Object.getPrototypeOf(spaghetti);  
  
// Add a property to the prototype and validate that  
// the original object has the property.  
proto.foodgroup = "carbohydrates";  
document.write(spaghetti.foodgroup + " ");  
  
// Verify that the prototype obtained from the object  
// is the same as the prototype of the constructor.  
var result = (proto === Pasta.prototype);  
document.write(result + " ");  
  
// Verify that prototype obtained from the object  
// is a prototype of the original object.  
var result = proto.isPrototypeOf(spaghetti);  
document.write(result);  
  
// Output: carbohydrates true true  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el `Object.getPrototypeOf` función para validar los tipos de datos.  
  
```JavaScript  
var reg = /a/;  
var result = (Object.getPrototypeOf(reg) === RegExp.prototype);  
document.write(result + " ");  
  
var err = new Error("an error");  
var result = (Object.getPrototypeOf(err) === Error.prototype);  
document.write(result);  
  
// Output: true true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [prototype (propiedad) (objeto)](../../javascript/reference/prototype-property-object-javascript.md)   
 [isPrototypeOf (Método, Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)