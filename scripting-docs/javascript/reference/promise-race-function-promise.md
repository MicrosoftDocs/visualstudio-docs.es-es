---
title: Función Promise.race (promesa) | Documentos de Microsoft
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d35c448ad143facdcd783df0551505e440521b98
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
ms.locfileid: "27782677"
---
# <a name="promiserace-function-promise"></a>Función Promise.race (promesa)
Crea una nueva promesa que resolverá o rechazará con el mismo valor de resultado que la primera promesa que se va resolver o rechazar entre los argumentos pasados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `iterable`  
 Requerido. Una o varias promesas.  
  
## <a name="remarks"></a>Comentarios  
 Si una de las promesas de `iterable` ya se encuentra en estado resuelto o rechazado, `Promise.race` devuelve una promesa resuelta o rechazada de la misma manera con el valor del resultado igual al valor que se usó para resolver (o rechazar) la promesa. Si varias promesas de `iterable` ya se resolvieron o rechazaron, `Promise.race` devuelve una promesa resuelta de la misma manera que la primera promesa iterada. Si no se resuelve o rechaza ninguna promesa de iterable, la promesa que se devuelve desde `Promise.race` tampoco se resuelve o rechaza.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p3 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)
