---
title: "Operador de suma (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operadores aritméticos, suma"
  - "cadenas [Visual Studio], concatenación"
  - "operadores de concatenación frente a operador de suma"
  - "operador de suma"
  - "+ (operador)"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Operador de suma (+) (JavaScript)
Suma el valor de una expresión numérica a otra, o concatena dos cadenas.  
  
## Sintaxis  
  
```  
  
result = expression1 + expression2  
```  
  
## Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## Comentarios  
 Los tipos de las dos expresiones determinan el comportamiento del operador **\+**.  
  
|Si|Entonces|  
|--------|--------------|  
|Ambas expresiones son numéricas o booleanas|Sumar|  
|Ambas expresiones son cadenas|Concatenar|  
|Una expresión es numérica y la otra es una cadena|Concatenar|  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación y suma \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)