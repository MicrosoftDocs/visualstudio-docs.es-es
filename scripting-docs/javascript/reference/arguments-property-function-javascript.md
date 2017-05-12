---
title: "arguments (Propiedad, Function de JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "argumentos, arguments (propiedad)"
  - "Arguments (propiedad)"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# arguments (Propiedad, Function de JavaScript)
Obtiene los argumentos del objeto `Function` que se está ejecutando actualmente.  
  
## Sintaxis  
  
```  
  
function.arguments  
```  
  
## Comentarios  
 El argumento `function` es el nombre de la función que se está ejecutando actualmente y se puede omitir.  
  
 Esta propiedad permite a una función controlar un número variable de argumentos.  La propiedad **length** del objeto `arguments` contiene el número de argumentos que se pasan a la función.  Se puede tener acceso a los argumentos individuales contenidos en el objeto `arguments` de la misma forma que a los elementos de una matriz.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `arguments`:  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [arguments \(Objeto\)](../../javascript/reference/arguments-object-javascript.md)   
 [function \(Instrucción\)](../../javascript/reference/function-statement-javascript.md)