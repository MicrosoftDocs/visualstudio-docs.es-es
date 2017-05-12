---
title: "Funci&#243;n Promise.reject (promesa) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funci&#243;n Promise.reject (promesa)
Crea una promesa rechazada nueva cuyo resultado es igual que el argumento pasado.  
  
## Sintaxis  
  
```  
Promise.reject(r);  
```  
  
#### Parámetros  
 `r`  
 Obligatorio.  Motivo por el que se rechazó la promesa.  
  
## Comentarios  
 La función de control de errores del método `then` o `catch` se ejecuta cuando se devuelve la promesa rechazada.  
  
## Ejemplo  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)