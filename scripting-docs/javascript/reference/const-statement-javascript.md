---
title: "const (Instrucci&#243;n, JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "declarar variables, instrucción const"
  - "const (instrucción)"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# const (Instrucci&#243;n, JavaScript)
Declara una variable de ámbito del bloque con un valor constante.  
  
## Sintaxis  
  
```  
const constant1 = value1  
```  
  
#### Parámetros  
 `constant1`  
 Nombre de la variable que se está declarando.  
  
 `value1`  
 Valor inicial asignado a la variable.  
  
## Comentarios  
 Utilice la instrucción `const` para declarar una variable con un valor constante, el ámbito del que está limitado al bloque en el que se declara.  El valor de la variable no se puede cambiar.  
  
 Una variable declarada con `const` debe inicializarse cuando se declara.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `const`.  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [let \(Instrucción\)](../../javascript/reference/let-statement-javascript.md)   
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)