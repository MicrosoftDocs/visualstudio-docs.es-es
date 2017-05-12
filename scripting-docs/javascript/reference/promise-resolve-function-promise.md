---
title: "Funci&#243;n Promise.resolve (Promise) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Funci&#243;n Promise.resolve (Promise)
Crea una promesa resuelta nueva cuyo resultado es igual que su argumento.  
  
## Sintaxis  
  
```  
Promise.resolve(x)  
```  
  
#### Parámetros  
 `x`  
 Obligatorio.  Valor devuelto con la promesa completada.  
  
## Comentarios  
 La función de control de cumplimiento del método `then` se ejecuta cuando se devuelve el objeto Promise completado.  
  
## Ejemplo  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vea también  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)