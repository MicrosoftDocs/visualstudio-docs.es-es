---
title: "Función Promise.Reject (promesa) | Documentos de Microsoft"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="promisereject-function-promise"></a>Función Promise.reject (promesa)
Crea una promesa rechazada nueva cuyo resultado es igual que el argumento pasado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `r`  
 Obligatorio. Motivo por el que se rechazó la promesa.  
  
## <a name="remarks"></a>Comentarios  
 La función de control de errores del método `then` o `catch` se ejecuta cuando se devuelve la promesa rechazada.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)