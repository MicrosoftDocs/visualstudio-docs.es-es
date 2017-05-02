---
title: "Math.log (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log (método)"
  - "Math (objeto)"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Math.log (Funci&#243;n de JavaScript)
Devuelve el logaritmo natural \(en base `e`\) de un número especificado.  
  
## Sintaxis  
  
```  
Math.log(number)   
```  
  
#### Parámetros  
 number  
 Un número.  
  
## Valor devuelto  
 Si `number` es positivo, esta función devuelve el logaritmo natural del número.  Si `number` es negativo, esta función devuelve `NaN`.  Si `number` es 0, esta función devuelve `-Infinity`.  
  
## Ejemplo  
 En el código siguiente se muestra cómo utilizar esta función.  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)  
  
## Vea también  
 [Math.sqrt \(Función\)](../../javascript/reference/math-sqrt-function-javascript.md)