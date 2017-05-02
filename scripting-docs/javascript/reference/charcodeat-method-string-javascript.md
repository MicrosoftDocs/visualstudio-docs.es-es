---
title: "charCodeAt (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt (método)"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# charCodeAt (M&#233;todo, String de JavaScript)
Devuelve el valor Unicode del carácter en la ubicación especificada.  
  
## Sintaxis  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## Parámetros  
 `strObj`  
 Obligatorio.  Cualquier objeto `String` o literal de cadena.  
  
 `index`  
 Obligatorio.  El índice de base cero del carácter deseado.  Si no hay ningún carácter en el índice especificado, se devuelve `NaN`.  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `charCodeAt`.  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [Función String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)