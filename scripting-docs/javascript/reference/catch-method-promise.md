---
title: "Método catch (Promise) | Documentos de Microsoft"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="catch-method-promise"></a>Método catch (Promise)
Permite especificar el trabajo que se va a realizar al rechazar una promesa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `promise`  
 Obligatorio. Objeto Promise.  
  
 `onRejected`  
 Obligatorio. Función de controlador de errores que se ejecuta cuando se rechaza una promesa.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente, la primera llamada a tiempo de espera se devuelve después de 5.000 ms. En este código, la promesa se rechaza y se ejecuta la función de controlador de errores.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]