---
title: "Operador l&#243;gico AND (&amp;&amp;) (JavaScript) | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&amp;&amp; (operador)"
  - "AND lógico (operador)"
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operador l&#243;gico AND (&amp;&amp;) (JavaScript)
Realiza una conjunción lógica de dos expresiones.  
  
## Sintaxis  
  
```  
  
result = expression1 && expression2   
```  
  
## Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## Comentarios  
 Si `expression1` se evalúa como `false`, `result` es `expression1`.  En caso contrario, `result` es `expression2`.  Por consiguiente, la operación devuelve `true` si ambos operandos son true; de lo contrario, devuelve `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa las reglas siguientes para convertir valores no booleanos en valores booleanos:  
  
-   Todos los objetos se consideran `true`.  
  
-   Las cadenas se consideran `false` si están vacías.  
  
-   `null` y `undefined` se consideran `false`.  
  
-   Un número es `false` si es cero.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)