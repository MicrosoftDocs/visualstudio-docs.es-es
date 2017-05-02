---
title: "toString (M&#233;todo, String) | Microsoft Docs"
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
ms.assetid: 56178c6e-cb08-4b34-824c-f63505379952
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString (M&#233;todo, String)
Devuelve una representación alfanumérica de una cadena.  
  
## Sintaxis  
  
```  
  
string.toString()  
```  
  
## Parámetros  
 `string`  
 Obligatorio.  Matriz que se va a representar como cadena.  
  
## Valor devuelto  
 Representación alfanumérica de la cadena.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **toString** con una cadena.  
  
```javascript  
var string = "this is a test";  
var strStr = string.toString();  
document.write(strStr);  
  
// Output: this is a test  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]