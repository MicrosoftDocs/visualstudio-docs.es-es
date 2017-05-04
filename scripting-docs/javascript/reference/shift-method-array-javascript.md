---
title: "shift (M&#233;todo, Array de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift (método)"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# shift (M&#233;todo, Array de JavaScript)
Quita el primer elemento de una matriz y lo devuelve.  
  
## Sintaxis  
  
```  
  
arrayObj.shift( )  
```  
  
#### Parámetros  
 La referencia `arrayObj` obligatoria es un objeto `Array`.  
  
## Valor devuelto  
 Devuelve el elemento quitado de la matriz.  
  
## Comentarios  
 En el ejemplo siguiente se muestra el uso del método `shift`.  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [unshift \(Método, Array\)](../../javascript/reference/unshift-method-array-javascript.md)