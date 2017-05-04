---
title: "valueOf (M&#233;todo, Boolean) | Microsoft Docs"
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
ms.assetid: ac6ad343-7663-406a-a2b7-4cc5025ca3d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf (M&#233;todo, Boolean)
Devuelve el valor primitivo del valor Boolean especificado.  
  
## Sintaxis  
  
```  
  
boolean.valueOf()  
```  
  
## Valor devuelto  
 Valor primitivo \(true o false\) del valor Boolean.  
  
## Comentarios  
 En el código siguiente se muestra cómo usar este método.  
  
```javascript  
var bool = new Boolean("true");  
var s = bool.valueOf();  
document.write(s);  
  
// Output: true  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]