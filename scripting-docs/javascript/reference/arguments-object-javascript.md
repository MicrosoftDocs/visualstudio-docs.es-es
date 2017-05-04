---
title: "arguments (Objeto de JavaScript) | Microsoft Docs"
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
  - "arguments (objeto)"
  - "argumentos, arguments (objeto)"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# arguments (Objeto de JavaScript)
Objeto que representa los argumentos de la función que se está ejecutando actualmente y las funciones que lo llamaron.  
  
## Sintaxis  
  
```  
[function.]arguments[n]  
```  
  
## Parámetros  
 *función*  
 Opcional.  Nombre del objeto `Function` que se ejecuta actualmente.  
  
 *n*  
 Requerido.  Índice de base cero de los valores de argumentos pasados al objeto `Function`.  
  
## Comentarios  
 No puede crear explícitamente un objeto **arguments**.  El objeto **arguments** solo está disponible cuando comienza la ejecución de una función.  Aunque el objeto **arguments** de la función no es una matriz, el acceso a los argumentos individuales se efectúa de la misma forma que a los elementos de una matriz.  El índice *n* es realmente una referencia a una de las propiedades **0** ***n*** del objeto **arguments**.  
  
## Ejemplo  
 El siguiente método muestra el uso del objeto **arguments**:  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [0...n \(Propiedades, arguments\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee \(Propiedad, arguments\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length \(Propiedad, argumentos\)](../../javascript/reference/length-property-arguments-javascript.md)