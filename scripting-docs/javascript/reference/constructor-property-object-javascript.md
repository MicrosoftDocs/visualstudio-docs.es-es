---
title: constructor (propiedad) (objeto) (JavaScript) | Documentos de Microsoft
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
- constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636265"
---
# <a name="constructor-property-object-javascript"></a>constructor (Propiedad, Object de JavaScript)
Especifica la función que crea un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `object` es el nombre de un objeto o función.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo. Esto incluye todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos excepto el `Global` y `Math` objetos. La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad de constructor.  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)