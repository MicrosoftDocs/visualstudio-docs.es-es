---
title: "break (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break (instrucción)"
  - "do...while (instrucción)"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# break (Instrucci&#243;n de JavaScript)
Finaliza el bucle actual o, si se usa junto con `label`, finaliza la instrucción asociada.  
  
## Sintaxis  
  
```  
break [label];  
```  
  
## Comentarios  
 El argumento `label` opcional especifica la etiqueta de la instrucción desde la que deseas interrumpir.  
  
 Normalmente, la instrucción `break` se usa en instrucciones `switch` y en bucles `while`, `for`, `for...in` o `do...while`.  Por lo general, el argumento `label` se usa en instrucciones `switch`, pero puedes usarlo en cualquier instrucción simple o compuesta.  
  
 Al ejecutar la instrucción `break` se sale del bucle o de la instrucción actual y comienza la ejecución del script con la instrucción que hay inmediatamente después.  
  
## Ejemplos  
 En este ejemplo, el contador está configurado para contar de 1 a 99; sin embargo, la instrucción `break` finaliza el bucle tras 14 iteraciones.  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 En el código siguiente, la instrucción `break` hace referencia al bucle `for` que va precedido de la instrucción `Inner:`.  Cuando `j` es igual a 24, la instrucción `break` hace que el flujo del programa salga de dicho bucle.  Se imprimen los números 21 a 23 en cada línea.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [continue \(Instrucción\)](../../javascript/reference/continue-statement-javascript.md)   
 [do...while \(Instrucción\)](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [for...in \(Instrucción\)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrucción con etiqueta](../../javascript/reference/labeled-statement-javascript.md)   
 [while \(Instrucción\)](../../javascript/reference/while-statement-javascript.md)