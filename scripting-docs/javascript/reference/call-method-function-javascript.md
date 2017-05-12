---
title: "call (M&#233;todo, Function de JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call (método)"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# call (M&#233;todo, Function de JavaScript)
Llama a un método de un objeto y sustituye el objeto actual por otro objeto.  
  
## Sintaxis  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## Parámetros  
 `thisObj`  
 Opcional.  Objeto que se va a utilizar como objeto actual.  
  
 `arg1, arg2, , argN`  
 Opcional.  Lista de argumentos que se van a pasar al método.  
  
## Comentarios  
 El método `call` se usa para llamar a un método en nombre de otro objeto.  Permite cambiar el objeto `this` de una función del contexto original al nuevo objeto especificado por  `thisObj`.  
  
 Si no se proporciona el argumento `thisObj`, el objeto `global` se utiliza como argumento `thisObj`.  
  
## Ejemplo  
 En el código siguiente se muestra cómo puede utilizar el método `call`.  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)   
 [apply \(Método, Function\)](../../javascript/reference/apply-method-function-javascript.md)