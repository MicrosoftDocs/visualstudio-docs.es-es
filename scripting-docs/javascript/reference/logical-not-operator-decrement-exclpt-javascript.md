---
title: "Operador l&#243;gico NOT (!) (JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! (operador)"
  - "! (operador), acerca del operador !"
  - "operador lógico NOT"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Operador l&#243;gico NOT (!) (JavaScript)
Realiza una negación lógica en una expresión.  
  
## Sintaxis  
  
```  
  
result = !expression  
```  
  
## Parámetros  
 *result*  
 Cualquier variable.  
  
 *expression*  
 Cualquier expresión.  
  
## Comentarios  
 En la tabla siguiente se indica cómo se determina *result*:  
  
|Si el valor de `expression` es|`result` es|  
|------------------------------------|-----------------|  
|True|False|  
|False|True|  
  
 Todos los operadores unarios, como el operador **\!**, evalúan las expresiones como se indica a continuación:  
  
-   Si se aplica a expresiones con valores sin definir o `null`, se genera un error en tiempo de ejecución.  
  
-   Los objetos se convierten en cadenas.  
  
-   Las cadenas se convierten en números, si es posible.  De lo contrario, se genera un error en tiempo de ejecución.  
  
-   Los valores de tipo Boolean se tratan como números \(0 si es false y 1 si es true\).  
  
 El operador se aplica al número resultante.  
  
 Para el operador **\!**, si el argumento *expression* es distinto de cero, el argumento *result* es cero.  Si *expression* es cero, *result* es 1.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Operador NOT bit a bit \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)