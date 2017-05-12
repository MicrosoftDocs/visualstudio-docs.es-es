---
title: "Operadores de incremento (++) y decremento (--) (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operadores de incremento, sintaxis"
  - "++ (operador)"
  - "operador ++, acerca del operador ++"
  - "operadores de decremento, sintaxis"
  - "-- (operador)"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operadores de incremento (++) y decremento (--) (JavaScript)
El operador de incremento incrementa, y el operador de decremento disminuye, el valor de una variable en uno.  
  
## Sintaxis  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## Parámetros  
 `result`  
 Cualquier variable.  
  
 `variable`  
 Cualquier variable.  
  
## Comentarios  
 Si el operador aparece antes de la variable, el valor se modifica antes de que se evalúe la expresión.  Si el operador aparece después de la variable, el valor se modifica después de que se evalúe la expresión.  Es decir, dado `j = ++k;`, el valor de `j` es el valor original de `k` más uno; dado `j = k++;`, el valor de `j` es el valor original de `k`, que se incrementa después de que su valor se asigne a `j`.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)