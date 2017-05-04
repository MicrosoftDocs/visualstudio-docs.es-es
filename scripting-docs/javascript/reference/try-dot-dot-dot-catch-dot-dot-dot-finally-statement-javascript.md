---
title: "try...catch...finally (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "control de excepciones try-catch"
  - "control de excepciones try-catch, acerca del control de excepciones try-catch"
  - "control de excepciones try-catch, bloque catch"
  - "control de excepciones try-catch, bloque finally"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# try...catch...finally (Instrucci&#243;n de JavaScript)
Configura bloques de código en los que los errores que se producen en un bloque se controlan en otro.  Los errores que se producen dentro del bloque `try` se detectan en el bloque `catch`.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Sintaxis  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## Parámetros  
 `tryStatements`  
 Obligatorio.  Instrucciones donde puede producirse un error.  
  
 `exception`  
 Obligatorio.  Cualquier nombre de variable.  El valor inicial de `exception` es el valor del error producido.  
  
 `catchStatements`  
 Opcional.  Instrucciones para controlar los errores que tienen lugar en los argumentos `tryStatements` asociados.  
  
 `finallyStatements`  
 Opcional.  Instrucciones que se ejecutan incondicionalmente después de que se hayan procesado todos los demás errores.  
  
## Comentarios  
 La instrucción `try...catch...finally` proporciona un medio para controlar una parte o la totalidad de los errores que pueden producirse en un bloque de código determinado, mientras se sigue ejecutando el código.  Si se producen errores no controlados, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] proporciona el mensaje de error normal.  
  
 El bloque `try` contiene código que puede provocar un error, mientras que el bloque `catch` contiene el código que controla todos o algunos de los errores.  Si se produce un error en el bloque `try`, el control de programas se pasa al bloque `catch`.  El valor inicial de `exception` es el valor del error que se produjo en el bloque `try`.  Si no se produce ningún error, no se ejecuta nunca el código del bloque `catch`.  
  
 Puede pasar el error hasta el nivel siguiente mediante la instrucción `throw` para volver a producir el error.  
  
 Después de que se ejecuten todas las instrucciones en el bloque `try` y se haya realizado un control de errores en el bloque `catch`, se ejecutan las instrucciones en el bloque `finally`, con independencia de si se ha controlado o no un error.  El código del bloque `finally` se ejecuta siempre, a menos que se produzca un error no controlado \(por ejemplo, un error en tiempo de ejecución en el bloque **catch**\).  
  
## Ejemplo  
 En el ejemplo siguiente se genera una excepción `ReferenceError` y se muestra el nombre del error y su mensaje.  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo volver a producir errores, así como la ejecución de bloques `try…catch` anidados.  Cuando el error se produce en el bloque anidado `try`, se pasa al bloque `catch` anidado, que vuelve a producirlo.  El bloque `finally` anidado se ejecuta antes que el bloque `catch` externo controle el error y al final se ejecuta el bloque externo `finally`.  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  A partir del modo estándar de Internet Explorer 8, el bloque **catch** ya no es necesario para que se ejecute `finally`.  
  
## Vea también  
 [throw \(Instrucción\)](../../javascript/reference/throw-statement-javascript.md)   
 [Aplicación de ejemplo del asistente para configuración de Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)