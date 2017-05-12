---
title: "Operador de asignaci&#243;n y suma (+=) (JavaScript) | Microsoft Docs"
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
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operador de asignación y suma (+=)"
  - "+= (operador)"
  - "operadores de asignación, JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operador de asignaci&#243;n y suma (+=) (JavaScript)
Suma el valor de una expresión al valor de una variable y asigna el resultado a la variable.  
  
## Sintaxis  
  
```  
  
result += expression   
```  
  
## Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression`  
 Cualquier expresión.  
  
## Comentarios  
 El uso de este operador es exactamente igual que si se especifica `result = result + expression`.  
  
 Los tipos de las dos expresiones determinan el comportamiento del operador `+=`.  
  
|Si|Entonces|  
|--------|--------------|  
|Ambas expresiones son numéricas o booleanas|Sumar|  
|Ambas expresiones son cadenas|Concatenar|  
|Una expresión es numérica y la otra es una cadena|Concatenar|  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de suma \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)