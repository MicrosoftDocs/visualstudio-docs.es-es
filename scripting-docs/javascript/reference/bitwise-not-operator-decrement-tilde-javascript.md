---
title: "Operador NOT bit a bit (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operadores bit a bit, NOT (operador)"
  - "NOT (operador)"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operador NOT bit a bit (~) (JavaScript)
Realiza una operación NOT \(negación\) bit a bit en una expresión.  
  
## Sintaxis  
  
```  
  
result = ~ expression  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression*  
 Cualquier expresión.  
  
## Comentarios  
 Todos los operadores unarios, como el operador `~`, evalúan las expresiones como se indica a continuación:  
  
-   Si se aplica a expresiones con valores sin definir o `null`, se genera un error en tiempo de ejecución.  
  
-   Los objetos se convierten en cadenas.  
  
-   Las cadenas se convierten en números, si es posible.  De lo contrario, se genera un error en tiempo de ejecución.  
  
-   Los valores de tipo Boolean se tratan como números \(0 si es false y 1 si es true\).  
  
 El operador se aplica al número resultante.  
  
 El operador `~` examina la representación binaria de los valores de la expresión y realiza una operación de negación bit a bit en ella.  
  
 Cualquier dígito que sea un 1 en la expresión se convierte en un 0 en el resultado.  Cualquier dígito que sea un 0 en la expresión se convierte en un 1 en el resultado.  
  
 En el ejemplo siguiente se muestra el uso del operador NOT bit a bit \(~\).  
  
```  
var temp = ~5;  
```  
  
 El valor resultante es \-6, como se muestra en la tabla siguiente.  
  
|Expresión|Valor binario \(complemento de dos\)|Valor decimal|  
|---------------|------------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador lógico NOT \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)