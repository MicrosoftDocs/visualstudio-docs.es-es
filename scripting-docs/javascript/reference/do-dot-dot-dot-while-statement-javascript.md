---
title: "do...while (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while (instrucción)"
  - "terminar bucles"
  - "estructuras de bucle, do y do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# do...while (Instrucci&#243;n de JavaScript)
Ejecuta un bloque de instrucciones una vez y, a continuación, repite la ejecución del bucle hasta que la evaluación de una expresión de condición devuelva `false`.  
  
## Sintaxis  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## Parámetros  
 `statement`  
 Requerido.  Instrucción que se va a ejecutar si `expression` es `true`.  Puede ser una instrucción compuesta.  
  
 `expression`  
 Requerido.  Expresión que se puede convertir en `true` o `false` booleano.  Si `expression` es `true`, el bucle se ejecuta de nuevo.  Si `expression` es `false`, finaliza el bucle.  
  
## Comentarios  
 A diferencia de la instrucción `while`, un bucle `do...while` se ejecuta una vez antes de que se evalúe la expresión condicional.  
  
 En cualquier línea de un bloque `do…while`, puede utilizar la instrucción `break` para que el programa salga del bucle o la instrucción `continue` para ir directamente a la expresión `while`.  
  
## Ejemplo  
 En el ejemplo siguiente, las instrucciones del bucle `do...while` se siguen ejecutando siempre y cuando la variable `i` sea menor que 10.  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## Ejemplo  
 En el ejemplo siguiente, las instrucciones del bucle se ejecutan una vez aunque la condición no se cumple.  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [break \(Instrucción\)](../../javascript/reference/break-statement-javascript.md)   
 [continue \(Instrucción\)](../../javascript/reference/continue-statement-javascript.md)   
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [for...in \(Instrucción\)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while \(Instrucción\)](../../javascript/reference/while-statement-javascript.md)   
 [Instrucción con etiqueta](../../javascript/reference/labeled-statement-javascript.md)