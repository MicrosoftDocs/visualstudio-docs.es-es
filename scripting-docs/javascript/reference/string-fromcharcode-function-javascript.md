---
title: "String.fromCharCode (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt (método)"
  - "caracteres, de Unicode"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# String.fromCharCode (Funci&#243;n de JavaScript)
Devuelve una cadena a partir de varios valores de caracteres Unicode.  
  
## Sintaxis  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## Parámetros  
 `String`  
 Obligatorio.  Objeto `String`.  
  
 `code1`, . . . , `codeN`  
 Opcional.  Serie de valores de caracteres Unicode que se van a convertir en una cadena.  Si no se proporciona ningún argumento, el resultado es una cadena vacía.  
  
## Comentarios  
 Llama a esta función en el objeto `String` en lugar de en una instancia de la cadena.  
  
 En el ejemplo siguiente se muestra cómo usar este método:  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [charCodeAt \(Método, String\)](../../javascript/reference/charcodeat-method-string-javascript.md)