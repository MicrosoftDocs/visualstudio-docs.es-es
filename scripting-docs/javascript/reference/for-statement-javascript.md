---
title: "for (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "estructuras de bucle, for (instrucciones)"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# for (Instrucci&#243;n de JavaScript)
Ejecuta un bloque de instrucciones mientras una condición especificada sea igual a True.  
  
## Sintaxis  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## Parámetros  
 `initialization`  
 Opcional.  Expresión.  Esta expresión se ejecuta solo una vez, antes de que se ejecute el bucle.  
  
 `test`  
 Opcional.  Expresión booleana.  Si `test` es `true`, se ejecuta `statement`.  Si `test` es `false`, finaliza el bucle.  
  
 `increment`  
 Opcional.  Expresión.  La expresión de incremento se ejecuta al final de cada ciclo del bucle.  
  
 `statement`  
 Opcional.  Una o más instrucciones que se ejecutarán si `test` es **true**.  Puede ser una instrucción compuesta.  
  
## Comentarios  
 Normalmente se usa un bucle `for` cuando el bucle se va a ejecutar un número conocido de veces.  Un bucle `for` es útil para recorrer en iteración matrices y realizar procesamientos secuenciales.  
  
 La comprobación de una expresión condicional tiene lugar antes de la ejecución del bucle, por lo que una instrucción `for` se ejecuta cero o más veces.  
  
 En cualquier línea del bloque de instrucciones de un bucle `for` puedes usar la instrucción `break` para salir del bucle o puedes usar la instrucción `continue` para transferir el control a la siguiente iteración del bucle.  
  
## Ejemplo  
 En el ejemplo siguiente, la instrucción `for` ejecuta las instrucciones entre paréntesis de la siguiente manera:  
  
-   Primero se evalúa el valor inicial de la variable `i`.  
  
-   A continuación, mientras el valor de `i` sea menor o igual que 9, se ejecutarán las instrucciones `document.write` y se volverá a evaluar `i`.  
  
-   Cuando el valor de `i` sea mayor que 9, la condición pasará a ser false y se transferirá el control fuera del bucle.  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## Ejemplo  
 Todas las expresiones de la instrucción `for` son opcionales.  En el ejemplo siguiente, las instrucciones `for` crean un bucle infinito y se usa una instrucción `break` para salir del bucle.  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [for...in \(Instrucción\)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while \(Instrucción\)](../../javascript/reference/while-statement-javascript.md)