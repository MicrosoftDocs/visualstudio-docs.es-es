---
title: "toPrecision (M&#233;todo, Number de JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision (método)"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toPrecision (M&#233;todo, Number de JavaScript)
Representa un número en notación exponencial o de punto fijo con un número especificado de dígitos.  
  
## Sintaxis  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## Parámetros  
 `numObj`  
 Obligatorio.  Un objeto `Number`.  
  
 `precision`  
 Opcional.  Número de dígitos significativos.  Debe estar entre 1 y 21, ambos incluidos.  
  
## Valor devuelto  
 En el caso de números representados en notación exponencial, se devuelven `precision` \- 1 dígitos detrás del signo decimal.  En el caso de números representados en notación fija, se devuelven `precision` dígitos significativos.  
  
 Si no se proporciona ningún valor para `precision` o si es **undefined**, se llama al método **toString** en su lugar.  
  
## Ejemplo  
 En el siguiente código se muestra cómo usar `toPrecision`.  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)  
  
## Vea también  
 [toFixed \(Método, Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential \(Método, Number\)](../../javascript/reference/toexponential-method-number-javascript.md)