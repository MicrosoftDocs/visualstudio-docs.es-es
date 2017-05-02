---
title: "valueOf (M&#233;todo, Number) | Microsoft Docs"
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf (M&#233;todo, Number)
Devuelve el valor primitivo del número especificado.  
  
## Sintaxis  
  
```  
  
number.valueOf()  
```  
  
#### Parámetros  
 Este método no tiene parámetros.  
  
## Valor devuelto  
 Devuelve el número.  
  
## Comentarios  
 En el ejemplo siguiente, el objeto number con instancias es igual que el valor devuelto de este método.  
  
```javascript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]