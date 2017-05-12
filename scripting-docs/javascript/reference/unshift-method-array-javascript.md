---
title: "unshift (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift (método)"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# unshift (M&#233;todo, Array de JavaScript)
Inserta nuevos elementos al principio de una matriz.  
  
## Sintaxis  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto `Array`.  
  
 `item1, item2,. . ., itemN`  
 Opcional.  Elementos que se van a insertar al principio de `Array`.  
  
## Comentarios  
 El método `unshift` inserta elementos al principio de una matriz, de forma que aparezcan en el mismo orden que tienen en la lista de argumentos.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `unshift`.  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [shift \(Método, Array\)](../../javascript/reference/shift-method-array-javascript.md)