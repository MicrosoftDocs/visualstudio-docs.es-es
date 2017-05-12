---
title: "return (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function (instrucción)"
  - "return (instrucción)"
  - "return (instrucción), salir de funciones en una secuencia de comandos"
  - "return (instrucción), sintaxis"
  - "terminar una ejecución"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# return (Instrucci&#243;n de JavaScript)
Sale de la función actual y devuelve un valor desde esa función.  
  
## Sintaxis  
  
```  
  
return[(][expression][)];   
```  
  
## Comentarios  
 El argumento opcional *expression* es el valor que se va a devolver desde la función.  Si se omite, la función no devuelve ningún valor.  
  
 La instrucción `return` se utiliza para detener la ejecución de una función y devolver el valor del argumento *expression*.  Si se omite esta *expresión*, o si no se ejecuta ninguna instrucción `return` desde la función, se asigna el valor undefined a la expresión que llamó a la función actual.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `return`.  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `return` para devolver una función.  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [function \(Instrucción\)](../../javascript/reference/function-statement-javascript.md)