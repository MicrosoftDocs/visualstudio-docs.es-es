---
title: "let (Instrucci&#243;n, JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let (instrucción)"
  - "declarar variables, instrucción let"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# let (Instrucci&#243;n, JavaScript)
Declara una variable de ámbito del bloque.  
  
## Sintaxis  
  
```  
let variable1 = value1  
```  
  
#### Parámetros  
 `variable1`  
 Nombre de la variable que se está declarando.  
  
 `value1`  
 Valor inicial asignado a la variable.  
  
## Comentarios  
 Utilice la instrucción `let` para declarar una variable, el ámbito del que está limitado al bloque en el que se declara.  Puede asignar valores a variables al declararlas o más adelante en el script.  
  
 Una variable declarada con `let` no puede usarse antes de que se active su declaración o un error.  
  
 Si no inicializa la variable en la instrucción `let`, se le asigna automáticamente el valor `undefined` de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `let`.  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [const \(Instrucción\)](../../javascript/reference/const-statement-javascript.md)   
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)