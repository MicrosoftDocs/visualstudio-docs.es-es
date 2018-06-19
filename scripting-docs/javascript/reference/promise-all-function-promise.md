---
title: Función Promise.All (Promise) | Documentos de Microsoft
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639915"
---
# <a name="promiseall-function-promise"></a>Función Promise.all (Promise)
Combina dos o más promesas y realiza la devolución solo cuando todas las promesas especificadas se completan o se rechazan.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `func1`  
 Obligatorio. Función que devuelve una promesa.  
  
 `func2`  
 Obligatorio. Función que devuelve una promesa.  
  
 `funcN`  
 Opcional. Una o más funciones que devuelven una promesa.  
  
## <a name="remarks"></a>Comentarios  
 El resultado devuelto es una matriz de valores devueltos por las promesas completadas. Si se rechaza una de las promesas combinadas, `Promise.all` realiza la devolución inmediatamente con la razón de la promesa rechazada (todos los demás valores devueltos se descartan).  
  
## <a name="example"></a>Ejemplo  
 En este código, la primera llamada a tiempo de espera se devuelve después de 5.000 ms. El controlador de finalización llama a `Promise.all`, que realiza la devolución solo cuando ambas llamadas al tiempo de espera se completan o se rechazan.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)