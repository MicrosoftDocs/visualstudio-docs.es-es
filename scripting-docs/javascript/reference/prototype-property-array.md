---
title: prototype (propiedad, Array) | Documentos de Microsoft
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd5102fe2f49218de76c498a11256a6ef24ff0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639015"
---
# <a name="prototype-property-array"></a>prototype (Propiedad, Array)
Devuelve una referencia al prototipo correspondiente a una clase de matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El `array` argumento es el nombre de una matriz.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `Array` que devuelva el valor del elemento más grande de la matriz, declare la función, agréguela a `Array.prototype` y después úsela.  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 Todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos tienen un `prototype` propiedad que es de solo lectura. Pueden agregar propiedades y métodos al prototipo, pero el objeto no puede asignarse a otro prototipo. Sin embargo, los objetos definidos por el usuario es posible asignar un nuevo prototipo.  
  
 Las listas de métodos y propiedades para cada objeto intrínseco en esta referencia del lenguaje indican que son parte del prototipo del objeto, y cuáles no.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]