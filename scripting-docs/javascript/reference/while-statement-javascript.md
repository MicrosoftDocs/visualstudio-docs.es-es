---
title: "while (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "estructuras de bucle, while (instrucciones)"
  - "while (instrucción)"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# while (Instrucci&#243;n de JavaScript)
Ejecuta una instrucción o una serie de instrucciones hasta que una condición especificada sea `false`.  
  
## Sintaxis  
  
```  
while (expression) {  
    statements  
}   
```  
  
## Parámetros  
 `expression`  
 Requerido.  Expresión booleana que se comprueba antes de cada iteración del bucle.  Si `expression` es `true`, el bucle se ejecuta.  Si `expression` es `false`, finaliza el bucle.  
  
 `statements`  
 Opcional.  Una o más instrucciones se van a ejecutar si `expression` es `true`.  
  
## Comentarios  
 La instrucción `while` comprueba el argumento `expression` antes de que se ejecute el bucle por primera vez.  Si `expression` es `false` en este momento, el bucle nunca llega a ejecutarse.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `while`.  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [break \(Instrucción\)](../../javascript/reference/break-statement-javascript.md)   
 [continue \(Instrucción\)](../../javascript/reference/continue-statement-javascript.md)   
 [do...while \(Instrucción\)](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [for...in \(Instrucción\)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)