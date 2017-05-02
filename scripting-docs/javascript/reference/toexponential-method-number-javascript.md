---
title: "toExponential (M&#233;todo, Number de JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential (Método)"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toExponential (M&#233;todo, Number de JavaScript)
Representa un número en notación exponencial.  
  
## Sintaxis  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## Parámetros  
 `numObj`  
 Obligatorio.  Objeto **Number**.  
  
 `fractionDigits`  
 Opcional.  Número de dígitos que hay después del signo decimal.  Debe estar entre 0 y 20, ambos incluidos.  
  
## Valor devuelto  
 Devuelve una representación alfanumérica de un número en notación exponencial.  La cadena contiene un dígito delante del signo decimal y puede contener `fractionDigits` dígitos detrás de él.  
  
 Si no proporcionas un valor para `fractionDigits`, el método `toExponential` devuelve el número de dígitos necesario para especificar el número de forma única.  
  
## Ejemplo  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)  
  
## Vea también  
 [toFixed \(Método, Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision \(Método, Number\)](../../javascript/reference/toprecision-method-number-javascript.md)