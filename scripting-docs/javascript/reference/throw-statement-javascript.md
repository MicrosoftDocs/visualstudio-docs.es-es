---
title: "throw (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "throw_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "control de errores, instrucción throw"
  - "throw (instrucción)"
ms.assetid: 75cbade0-fb81-4ffe-b187-b71be380bb05
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# throw (Instrucci&#243;n de JavaScript)
Genera una condición de error que se puede controlar con una instrucción `try...catch...finally`.  
  
## Sintaxis  
  
```  
throw exception   
```  
  
## Comentarios  
 El argumento obligatorio `exception` puede ser cualquier expresión.  
  
 En el ejemplo siguiente se produce un error en un bloque `try` y se detecta en el bloque `catch`.  
  
```javascript  
try {  
        throw new Error(200, "x equals zero");  
}  
catch (e) {  
    document.write(e.message);  
}  
  
// Output: x equals zero.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [try...catch...finally \(Instrucción\)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)