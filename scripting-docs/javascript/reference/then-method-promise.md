---
title: Método Then (promesa) | Documentos de Microsoft
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640215"
---
# <a name="then-method-promise"></a>Método then (promesa)
Permite especificar el trabajo que se va a realizar al cumplir una promesa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `promise`  
 Obligatorio. Objeto Promise.  
  
 `onCompleted`  
 Obligatorio. Función de controlador de cumplimiento que se ejecutará cuando la promesa se complete correctamente.  
  
 `onRejected`  
 Opcional. Función de controlador de errores que se ejecuta cuando se rechaza la promesa.  
  
## <a name="remarks"></a>Comentarios  
 Una promesa debe completarse con un valor o debe rechazarse con un motivo. El método `then` del objeto Promise se ejecuta cuando la promesa se completa o se rechaza, lo que ocurra primero. Si la promesa se completa correctamente, se ejecuta la función de controlador de cumplimiento del método `then`. Si la promesa se rechaza, se ejecuta la función de controlador de errores del método `then` (o el método `catch`).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo llamar a una función (`timeout`) que devuelve una promesa. El controlador de cumplimiento del método `then` se ejecuta después de que expire el período de tiempo de espera de 5.000 ms.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)