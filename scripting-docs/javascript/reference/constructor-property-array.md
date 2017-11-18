---
title: constructor (propiedad, Array) | Documentos de Microsoft
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca779a2fa2356c1f3e1ca816f16531c0930459a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-array"></a>constructor (Propiedad, Array)
Especifica la función que crea una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array.constructor  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `array` es el nombre de una matriz.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo. Esto incluye todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos excepto el `Global` y `Math` objetos. La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad de constructor.  
  
```JavaScript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]