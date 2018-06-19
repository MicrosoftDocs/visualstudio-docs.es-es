---
title: __proto__ (propiedad) (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8659c7a4ece5e30378838f20341ec6712f77ca3
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899580"
---
# <a name="proto-property-object-javascript"></a>__proto__ (propiedad) (objeto) (JavaScript)
Contiene una referencia al prototipo interno del objeto especificado.  

> [!WARNING]
> El `__proto__` propiedad es una característica heredada. Use [Object.getPrototypeOf](../reference/object-getprototypeof-function-javascript.md) en su lugar.
  
## <a name="syntax"></a>Sintaxis  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Requerido. Objeto en el que se va a establecer el prototipo.  
  
## <a name="remarks"></a>Comentarios  
 El `__proto__` propiedad puede utilizarse para establecer el prototipo de un objeto.  
  
 El objeto o función hereda todos los métodos y propiedades del nuevo prototipo junto con todos los métodos y propiedades de cadena de prototipo del nuevo prototipo. Un objeto puede tener solo un prototipo único (sin incluir los prototipos heredados en la cadena de prototipo), por lo que cuando se llama a la `__proto__` propiedad, reemplace el prototipo anterior.  
  
 Sólo puede establecer el prototipo en un objeto extensible. Para obtener más información, consulte [Object.preventExtensions (función)](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  El `__proto__` nombre de la propiedad empieza y termina con dos caracteres de subrayado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo establecer el prototipo de un objeto.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar propiedades a un objeto agregándolas al prototipo.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se agregan propiedades al objeto `String` estableciendo un nuevo prototipo en él.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Prototipos y herencia de prototipos](../../javascript/advanced/prototypes-and-prototype-inheritance.md)