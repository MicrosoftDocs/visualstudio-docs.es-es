---
title: "Funci&#243;n Promise.all (Promise) | Microsoft Docs"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funci&#243;n Promise.all (Promise)
Combina dos o más promesas y realiza la devolución solo cuando todas las promesas especificadas se completan o se rechazan.  
  
## Sintaxis  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### Parámetros  
 `func1`  
 Obligatorio.  Función que devuelve una promesa.  
  
 `func2`  
 Obligatorio.  Función que devuelve una promesa.  
  
 `funcN`  
 Opcional.  Una o más funciones que devuelven una promesa.  
  
## Comentarios  
 El resultado devuelto es una matriz de valores devueltos por las promesas completadas.  Si se rechaza una de las promesas combinadas, `Promise.all` realiza la devolución inmediatamente con la razón de la promesa rechazada \(todos los demás valores devueltos se descartan\).  
  
## Ejemplo  
 En este código, la primera llamada a tiempo de espera se devuelve después de 5.000 ms.  El controlador de finalización llama a `Promise.all`, que realiza la devolución solo cuando ambas llamadas al tiempo de espera se completan o se rechazan.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)