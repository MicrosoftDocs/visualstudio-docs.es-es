---
title: "Funci&#243;n Promise.race (promesa) | Microsoft Docs"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Funci&#243;n Promise.race (promesa)
Crea una nueva promesa que resolverá o rechazará con el mismo valor de resultado que la primera promesa que se va resolver o rechazar entre los argumentos pasados.  
  
## Sintaxis  
  
```  
Promise.race(iterable)  
  
```  
  
#### Parámetros  
 `iterable`  
 Obligatorio.  Una o varias promesas.  
  
## Comentarios  
 Si una de las promesas de `iterable` ya se encuentra en estado resuelto o rechazado, `Promise.race` devuelve una promesa resuelta o rechazada de la misma manera con el valor del resultado igual al valor que se usó para resolver \(o rechazar\) la promesa.  Si varias promesas de `iterable` ya se resolvieron o rechazaron, `Promise.race` devuelve una promesa resuelta de la misma manera que la primera promesa iterada.  Si no se resuelve o rechaza ninguna promesa de iterable, la promesa que se devuelve desde `Promise.race` tampoco se resuelve o rechaza.  
  
## Ejemplo  
  
```javascript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
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
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)