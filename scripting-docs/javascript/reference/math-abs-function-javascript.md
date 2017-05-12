---
title: "Math.abs (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valores absolutos, calcular"
  - "valores absolutos"
  - "expresiones numéricas"
  - "abs (método)"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Math.abs (Funci&#243;n de JavaScript)
Devuelve el valor absoluto de un número \(el valor independientemente de si es positivo o negativo\).  Por ejemplo, el valor absoluto de \-5 es el mismo que el valor absoluto de 5.  
  
## Sintaxis  
  
```  
Math.abs(number)  
```  
  
#### Parámetros  
 El argumento obligatorio `number` es una expresión numérica cuyo valor absoluto desea obtener.  
  
## Valor devuelto  
 Valor absoluto del argumento `number`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `abs`.  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)  
  
## Vea también  
 [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)