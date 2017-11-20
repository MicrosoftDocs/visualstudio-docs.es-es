---
title: "prototype (propiedad) (número) | Documentos de Microsoft"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-number"></a>prototype (Propiedad, Number)
Devuelve una referencia al prototipo correspondiente a una clase de número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `number` argumento es el nombre de un número.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método a la `Number` que devuelve los dígitos del números de (entero) del objeto, declare la función, agréguela a `Number.prototype`y, a continuación, usarla.  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos tienen un `prototype` propiedad que es de solo lectura. Pueden agregar propiedades y métodos al prototipo, pero el objeto no puede asignarse a otro prototipo. Sin embargo, los objetos definidos por el usuario es posible asignar un nuevo prototipo.  
  
 Las listas de métodos y propiedades para cada objeto intrínseco en esta referencia del lenguaje indican que son parte del prototipo del objeto, y cuáles no.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]