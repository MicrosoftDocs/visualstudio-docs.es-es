---
title: "M&#233;todo entries (matriz) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9bc46afb-74d2-4f99-8c95-f46475acf21d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo entries (matriz) (JavaScript)
Devuelve un iterador que devuelve los pares clave\-valor de la matriz.  
  
## Sintaxis  
  
```  
arrayObj.entries();  
```  
  
#### Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto de matriz.  
  
## Comentarios  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo obtener los pares clave\-valor de una matriz.  
  
```javascript  
var entries = ["a", "b", "c"].entries();  
// entries.next().value == [0, "a"]  
// entries.next().value == [1, "b"]  
// entries.next().value == [2, "c"]   
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]