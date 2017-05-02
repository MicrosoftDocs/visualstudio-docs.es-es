---
title: "Operador de resta (-) (JavaScript) | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- (operador)"
  - "- (operador), acerca del operador -"
  - "operadores aritméticos, resta"
  - "operador de negación"
  - "operadores, resta"
  - "operador de resta, sintaxis"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Operador de resta (-) (JavaScript)
Resta el valor de una expresión de otra o proporciona el valor unario de negación de una única expresión.  
  
## Sintaxis  
  
```  
  
result = number1 - number2;  
  
```  
  
## Parámetros  
 *result*  
 Cualquier variable numérica.  
  
 `number`  
 Cualquier expresión numérica.  
  
 `number1`  
 Cualquier expresión numérica.  
  
 `number2`  
 Cualquier expresión numérica.  
  
## Comentarios  
 En la sintaxis 1, el operador **\-** es el operador aritmético de resta usado para encontrar la diferencia entre dos números.  En la sintaxis 2, el operador **\-** se usa como operador unario de negación para indicar el valor negativo de una expresión.  
  
 Para la sintaxis 2, como para todos los operadores unarios, las expresiones se evalúan del modo siguiente:  
  
-   Si se aplica a expresiones con valores sin definir o `null`, se genera un error en tiempo de ejecución.  
  
-   Los objetos se convierten en cadenas.  
  
-   Las cadenas se convierten en números, si es posible.  De lo contrario, se genera un error en tiempo de ejecución.  
  
-   Los valores de tipo Boolean se tratan como números \(0 si es false y 1 si es true\).  
  
 El operador se aplica al número resultante.  En la sintaxis 2, si el número resultante es distinto de cero, el argumento *result* tiene un valor igual al número resultante con el signo contrario.  Si el número resultante es cero, el argumento *result* tiene un valor igual a cero.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador de asignación y sustracción \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)