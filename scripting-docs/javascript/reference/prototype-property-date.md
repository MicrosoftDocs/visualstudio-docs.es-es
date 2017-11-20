---
title: prototype (propiedad) (fecha) | Documentos de Microsoft
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>prototype (Propiedad, Date)
Devuelve una referencia al prototipo correspondiente a una fecha.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento de `date` es el nombre de un objeto.  
  
 Use la `prototype` propiedad para proporcionar un conjunto básico de funcionalidades a una fecha. Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `Date` que devuelva el valor del elemento más grande de la matriz, declare la función, agréguela a `Date.prototype` y después úsela.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos tienen un `prototype` propiedad que es de solo lectura. Pueden agregar propiedades y métodos al prototipo, pero el objeto no puede asignarse a otro prototipo. Sin embargo, los objetos definidos por el usuario es posible asignar un nuevo prototipo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]