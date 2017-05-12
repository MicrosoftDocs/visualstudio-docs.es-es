---
title: "M&#233;todo values (matriz) (JavaScript) | Microsoft Docs"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo values (matriz) (JavaScript)
Devuelve un iterador que devuelve los valores de la matriz.  
  
## Sintaxis  
  
```  
arrayObj.values();  
```  
  
#### Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto de matriz.  
  
## Comentarios  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo obtener los valores de una matriz.  
  
```javascript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]