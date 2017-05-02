---
title: "Array.isArray (Funci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array.isArray (función) [JavaScript]"
  - "isArray (función) [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Array.isArray (Funci&#243;n de JavaScript)
Determina si un objeto es una matriz.  
  
## Sintaxis  
  
```  
Array.isArray(object)   
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto que se va a probar.  
  
## Valor devuelto  
 Es `true` si `object` es una matriz; en caso contrario, es `false`.  Si el argumento `object` no es un objeto, se devuelve `false`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Array.isArray`.  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof \(Operador\)](../../javascript/reference/typeof-operator-decrementjavascript.md)