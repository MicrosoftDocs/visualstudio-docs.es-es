---
title: constructor (propiedad, String) | Documentos de Microsoft
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636065"
---
# <a name="constructor-property-string"></a>constructor (Propiedad, String)
Especifica la función que crea una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `string` es el nombre de una cadena.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo. Esto incluye todos los intrínsecos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos excepto el `Global` y `Math` objetos. La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad de constructor.  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]