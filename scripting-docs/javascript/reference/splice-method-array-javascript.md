---
title: "splice (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice (método)"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# splice (M&#233;todo, Array de JavaScript)
Quita elementos de una matriz, inserta nuevos elementos en su lugar si procede y devuelve los elementos eliminados.  
  
## Sintaxis  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto `Array`.  
  
 `start`  
 Obligatorio.  Ubicación basada en cero de la matriz desde la que se va a comenzar a quitar elementos.  
  
 `deleteCount`  
 Obligatorio.  Número de elementos que se va a quitar.  
  
 `item1, item2,. . ., itemN`  
 Opcional.  Elementos que se van a insertar en la matriz en lugar de los elementos eliminados.  
  
## Comentarios  
 El método `splice` modifica `arrayObj` quitando el número especificado de elementos desde la posición `start` e insertando elementos nuevos.  Los elementos eliminados se devuelven como un nuevo objeto `Array`.  
  
## Ejemplo  
 En el código siguiente se muestra cómo utilizar el método `splice`.  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [slice \(Método, Array\)](../../javascript/reference/slice-method-array-javascript.md)