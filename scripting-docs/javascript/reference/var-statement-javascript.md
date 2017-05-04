---
title: "var (Instrucci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "declarar variables, instrucción var"
  - "var (instrucción)"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# var (Instrucci&#243;n de JavaScript)
Declara una variable.  
  
## Sintaxis  
  
```  
var variable1 = value1  
```  
  
## Parámetros  
 `variable1`  
 Nombre de la variable que se está declarando.  
  
 `value1`  
 Valor inicial asignado a la variable.  
  
## Comentarios  
 Utilice la instrucción `var` para declarar variables.  Puede asignar valores a variables al declararlas o más adelante en el script.  
  
 Una variable se declara la primera vez que aparece en el script.  
  
 Puede declarar una variable sin usar la palabra clave `var` y asignarle un valor.  Esto es lo que se denomina una *declaración implícita* y no es recomendable.  Una declaración implícita aplica a la variable un ámbito global.  Sin embargo, al declarar una variable en un procedimiento, normalmente no es conveniente que tenga ámbito global.  Para evitar asignar a la variable el ámbito global, debe usar la palabra clave `var` en la declaración de variable.  
  
 Si no inicializa la variable en la instrucción `var`, se le asigna automáticamente el valor `undefined` de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Ejemplo  
 En los ejemplos siguientes se muestra el uso de la instrucción `var`.  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [function \(Instrucción\)](../../javascript/reference/function-statement-javascript.md)   
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)