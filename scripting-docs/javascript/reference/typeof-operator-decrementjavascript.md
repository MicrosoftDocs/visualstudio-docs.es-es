---
title: "typeof (Operador de JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof (operador)"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# typeof (Operador de JavaScript)
Devuelve una cadena que identifica el tipo de datos de una expresión.  
  
## Sintaxis  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## Comentarios  
 El argumento *expression* es cualquier expresión para la que se busca información de tipo.  
  
 El operador `typeof` devuelve información acerca del tipo en forma de cadena.  `typeof` devuelve seis valores posibles: "number", "string", "boolean", "object", "function" y "undefined".  
  
 Los paréntesis son opcionales en la sintaxis de `typeof`.  
  
## Ejemplo  
 En el ejemplo siguiente se prueba el tipo de datos de las variables.  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## Ejemplo  
 En el ejemplo siguiente se prueba si hay un tipo de datos `undefined` en las variables declaradas y sin declarar.  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Array.isArray \(Función\)](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf \(Función\)](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined \(Constante\)](../../javascript/reference/undefined-constant-javascript.md)   
 [Operadores de comparación](../../javascript/reference/comparison-operators-javascript.md)   
 [Tipos de datos](../../javascript/data-types-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)