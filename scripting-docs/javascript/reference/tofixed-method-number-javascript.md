---
title: "toFixed (M&#233;todo, Number de JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed (Método)"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# toFixed (M&#233;todo, Number de JavaScript)
Representa un número en notación de punto fijo.  
  
## Sintaxis  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## Parámetros  
 `numObj`  
 Se requiere un objeto `Number`.  
  
 `fractionDigits`  
 Opcional.  Número de dígitos que hay después del signo decimal.  Debe estar entre 0 y 20, ambos incluidos.  
  
## Valor devuelto  
 Devuelve una representación de cadena de un número en notación de punto fijo, que contiene dígitos de `fractionDigits` después de la coma decimal.  
  
 Si no se proporciona `fractionDigits` o es **undefined**, el valor predeterminado es cero.  
  
## Ejemplo  
 En el siguiente código se muestra cómo usar `toFixed`.  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)  
  
## Vea también  
 [toExponential \(Método, Number\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision \(Método, Number\)](../../javascript/reference/toprecision-method-number-javascript.md)