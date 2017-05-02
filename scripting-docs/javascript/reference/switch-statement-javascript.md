---
title: "switch (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch (instrucción)"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# switch (Instrucci&#243;n de JavaScript)
Permite la ejecución de una o más instrucciones cuando el valor de una expresión especificada coincide con una etiqueta.  
  
## Sintaxis  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## Parámetros  
 `expression`  
 Expresión que se va a evaluar.  
  
 `label`  
 Identificador con el que se compara `expression`.  Si `label` es `expression`, la ejecución empieza con `statementlist` que hay inmediatamente después del signo de dos puntos y continúa hasta que encuentra una instrucción `break`, que es opcional, o el final de la instrucción `switch`.  
  
 `statementlist`  
 Instrucción o instrucciones que se van a ejecutar.  
  
## Comentarios  
 Usa la cláusula `default` para proporcionar una instrucción que se ejecutará si ninguno de los valores de etiqueta coincide con `expression`.  Puede aparecer en cualquier lugar del bloque de código de `switch`.  
  
 Se pueden especificar cero o más bloques `label`.  Si ninguno de los argumentos `label` coincide con el valor de `expression` y no se proporciona una cláusula `default`, no se ejecuta ninguna instrucción.  
  
 La ejecución fluye por una instrucción `switch` de la siguiente manera:  
  
-   Evalúa `expression` y examina `label` por orden hasta encontrar una coincidencia.  
  
-   Si un valor de `label` es igual a `expression`, ejecuta la `statementlist` que lo acompaña.  
  
     La ejecución continúa hasta que se encuentra una instrucción `break` o hasta que la instrucción `switch` finaliza.  Esto implica la ejecución de varios bloques `label` si no se usa una instrucción `break`.  
  
-   Si ningún valor de `label` es igual a `expression`, va a la cláusula `default`.  Si no hay ninguna cláusula `default`, va al último paso.  
  
-   La ejecución continúa en la instrucción que sigue al final del bloque de código `switch`.  
  
## Ejemplo  
 En el ejemplo siguiente se comprueba el tipo de un objeto.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Ejemplo  
 En el código siguiente se muestra lo que ocurre si no usas una instrucción `break`.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [break \(Instrucción\)](../../javascript/reference/break-statement-javascript.md)   
 [if...else \(Instrucción\)](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)