---
title: "apply (M&#233;todo, Function de JavaScript) | Microsoft Docs"
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
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Apply (método)"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# apply (M&#233;todo, Function de JavaScript)
Llama a la función, sustituyendo el objeto especificado por el valor de `this` de la función, y la matriz especificada por los argumentos de la función.  
  
## Sintaxis  
  
```  
apply([thisObj[,argArray]])  
```  
  
## Parámetros  
 `thisObj`  
 Opcional.  Objeto que se va a usar como objeto `this`.  
  
 `argArray`  
 Opcional.  Conjunto de argumentos que se van a pasar a la función.  
  
## Comentarios  
 Si `argArray` no es un objeto válido, aparecerá un error de tipo “Se esperaba un objeto”.  
  
 Si no se proporcionan `argArray` ni `thisObj`, el objeto `this` original se usa como `thisObj` y no se pasan argumentos.  
  
## Ejemplo  
 En el código siguiente se muestra cómo utilizar el método apply.  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)