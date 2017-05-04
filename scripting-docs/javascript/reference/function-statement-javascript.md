---
title: "function (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "declarar funciones"
  - "declarar funciones, sintaxis"
  - "function (instrucción)"
  - "new (operador)"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# function (Instrucci&#243;n de JavaScript)
Declara una nueva función.  
  
## Sintaxis  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## Parámetros  
 `functionname`  
 Obligatorio.  Nombre de la función.  
  
 `arg1...argN`  
 Opcional.  Lista opcional separada por comas de argumentos que la función entiende.  
  
 `statements`  
 Opcional.  Una o más instrucciones de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Comentarios  
 Usa la instrucción `function` para declarar una función para su uso posterior.  El código contenido en `statements` no se ejecuta hasta que se llama a la función desde cualquier otro lugar del script.  
  
 La instrucción [return](../../javascript/reference/return-statement-javascript.md) se usa para devolver un valor de la función.  No es necesario usar ninguna instrucción `return`; el programa volverá cuando llegue al final de la función.  Si no se ejecuta ninguna instrucción `return` en la función, o si la instrucción `return` no tiene ninguna expresión, la función devuelve el valor `undefined`.  
  
> [!NOTE]
>  Cuando llames a una función, asegúrate de incluir los paréntesis y cualquier argumento necesario.  Al llamar a una función sin paréntesis se devuelve una referencia a la función, no los resultados de la función.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la instrucción `function`.  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## Ejemplo  
 Se puede asignar una función a una variable.  Esto se muestra en el ejemplo siguiente.  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)