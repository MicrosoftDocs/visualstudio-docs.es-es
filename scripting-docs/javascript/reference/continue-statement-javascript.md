---
title: "continue (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue (instrucción)"
  - "do...while (instrucción)"
  - "estructuras de bucle, continue (instrucción)"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# continue (Instrucci&#243;n de JavaScript)
Detiene la iteración actual de un bucle e inicia una nueva iteración.  
  
## Sintaxis  
  
```  
continue [label];  
```  
  
## Comentarios  
 El argumento `label` opcional especifica la instrucción a la que `continue` se aplica.  
  
 Solo puedes usar la instrucción `continue` dentro de un bucle `while`, `do...while`, **for** o `for...in`.  Al ejecutar la instrucción `continue` se detiene la iteración actual del bucle y el flujo del programa continúa al principio del bucle.  Esta acción tiene los siguientes efectos en los distintos tipos de bucle:  
  
-   Los bucles `while` y `do...while` comprueban su condición y, si es igual a true, vuelven a ejecutar el bucle.  
  
-   Los bucles `for` ejecutan su expresión de incremento y, si la expresión de comprobación es igual a true, vuelven a ejecutar el bucle.  
  
-   Los bucles `for...in` continúan en el siguiente campo de la variable especificada y vuelven a ejecutar el bucle.  
  
## Ejemplos  
 En este ejemplo, un bucle itera de 1 a 9.  Las instrucciones que hay entre `continue` y el final del cuerpo de `for` se omiten debido al uso de la instrucción `continue` junto con la expresión `(i < 5)`.  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 En el código siguiente, la instrucción `continue` hace referencia al bucle `for` que va precedido de la etiqueta `Inner:`.  Cuando `j` es 24, la instrucción `continue` hace que ese bucle `for` vaya a la siguiente iteración.  Se imprimen los números 21 a 23 y 25 a 30 en cada línea.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [break \(Instrucción\)](../../javascript/reference/break-statement-javascript.md)   
 [do...while \(Instrucción\)](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [for...in \(Instrucción\)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrucción con etiqueta](../../javascript/reference/labeled-statement-javascript.md)   
 [while \(Instrucción\)](../../javascript/reference/while-statement-javascript.md)