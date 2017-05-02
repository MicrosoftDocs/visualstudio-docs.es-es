---
title: "valueOf (M&#233;todo, Array) | Microsoft Docs"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf (M&#233;todo, Array)
Devuelve el valor primitivo del objeto especificado.  
  
## Sintaxis  
  
```  
  
array.valueOf()  
```  
  
#### Parámetros  
 Este método no tiene parámetros.  
  
## Valor devuelto  
 Devuelve la instancia de la matriz.  
  
## Comentarios  
 En el ejemplo siguiente, el objeto array con instancias es igual que el valor devuelto de este método.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]