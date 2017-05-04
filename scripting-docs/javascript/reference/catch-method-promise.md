---
title: "M&#233;todo catch (Promise) | Microsoft Docs"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# M&#233;todo catch (Promise)
Permite especificar el trabajo que se va a realizar al rechazar una promesa.  
  
## Sintaxis  
  
```  
  
promise.catch(onRejected)  
```  
  
#### Parámetros  
 `promise`  
 Obligatorio.  Objeto Promise.  
  
 `onRejected`  
 Obligatorio.  Función de controlador de errores que se ejecuta cuando se rechaza una promesa.  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo de código siguiente, la primera llamada a tiempo de espera se devuelve después de 5.000 ms.  En este código, la promesa se rechaza y se ejecuta la función de controlador de errores.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]