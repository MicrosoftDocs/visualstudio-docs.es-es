---
title: "Operador condicional ternario (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operador condicional ternario"
  - "operadores condicionales"
  - "ternario"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operador condicional ternario (?:) (JavaScript)
Devuelve una de las dos expresiones posibles, dependiendo de una condición.  
  
## Sintaxis  
  
```  
  
test ? expression1 : expression2  
```  
  
## Parámetros  
 `test`  
 Cualquier expresión booleana.  
  
 `expression1`  
 Expresión que se devuelve si `test` es `true`.  Puede ser una expresión de coma.  
  
 `expression2`  
 Expresión que se devuelve si `test` es `false`.  Se puede vincular más de una expresión mediante una expresión de coma.  
  
## Comentarios  
 El operador `?:` se puede utilizar como forma abreviada de una instrucción `if...else`.  Se utiliza normalmente como parte de una expresión mayor en la que una instrucción `if...else` no sería práctica.  Por ejemplo:  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 En el ejemplo se crea una cadena que contiene "Good evening" si es más tarde de las 6 p.m.  El código equivalente que utiliza una instrucción `if...else` tendría el siguiente aspecto:  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [if...else \(Instrucción\)](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Aplicación de ejemplo del widget de configuración de Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)