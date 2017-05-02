---
title: "M&#233;todo keys (matriz) (JavaScript) | Microsoft Docs"
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo keys (matriz) (JavaScript)
Devuelve un iterador que devuelve los valores de índice de la matriz.  
  
## Sintaxis  
  
```  
arrayObj.keys();  
```  
  
#### Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto de matriz.  
  
## Comentarios  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo obtener los valores de clave de una matriz.  
  
```javascript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]