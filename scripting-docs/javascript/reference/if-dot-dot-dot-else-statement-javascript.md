---
title: "if...else (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if (instrucción), if...else"
  - "estructuras de bucle, if...else (instrucciones)"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# if...else (Instrucci&#243;n de JavaScript)
Ejecuta condicionalmente un grupo de instrucciones en función del valor de una expresión.  
  
## Sintaxis  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## Parámetros  
 `condition1`  
 Obligatorio.  Expresión booleana.  Si `condition1` es `null` o `undefined`, `condition1` se trata como `false`.  
  
 `statement1`  
 Opcional.  Instrucción que se va a ejecutar si `condition1` es **true**.  Puede ser una instrucción compuesta.  
  
 `condition2`  
 Condición que se va a evaluar.  
  
 `statement2`  
 Opcional.  Instrucción que se va a ejecutar si `condition2` es `true`.  Puede ser una instrucción compuesta.  
  
 `statement3`  
 Si `condition1` y `condition2` son `false`, se ejecuta esta instrucción.  
  
## Ejemplo  
 En el código siguiente se muestra cómo usar `if`, `if else` y `else`.  
  
 Es conveniente poner `statement1` y `statement2` entre llaves \({}\) en aras de una mayor claridad y para evitar errores inadvertidos.  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador condicional ternario \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)