---
title: "M&#233;todo then (promesa) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# M&#233;todo then (promesa)
Permite especificar el trabajo que se va a realizar al cumplir una promesa.  
  
## Sintaxis  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### Parámetros  
 `promise`  
 Obligatorio.  Objeto Promise.  
  
 `onCompleted`  
 Obligatorio.  Función de controlador de cumplimiento que se ejecutará cuando la promesa se complete correctamente.  
  
 `onRejected`  
 Opcional.  Función de controlador de errores que se ejecuta cuando se rechaza la promesa.  
  
## Comentarios  
 Una promesa debe completarse con un valor o debe rechazarse con un motivo.  El método `then` del objeto Promise se ejecuta cuando la promesa se completa o se rechaza, lo que ocurra primero.  Si la promesa se completa correctamente, se ejecuta la función de controlador de cumplimiento del método `then`.  Si la promesa se rechaza, se ejecuta la función de controlador de errores del método `then` \(o el método `catch`\).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo llamar a una función \(`timeout`\) que devuelve una promesa.  El controlador de cumplimiento del método `then` se ejecuta después de que expire el período de tiempo de espera de 5000 ms.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)