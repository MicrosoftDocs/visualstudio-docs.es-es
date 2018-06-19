---
title: constructor (propiedad) (Error) | Documentos de Microsoft
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1ade0ab1ba771b2ff9dfb7051b2983b3da77ed4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636025"
---
# <a name="constructor-property-error"></a>constructor (Propiedad, Error)
Especifica la función que crea un Error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
error.constructor  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `error` es el nombre de un objeto de error.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo. La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad de constructor.  
  
```JavaScript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]