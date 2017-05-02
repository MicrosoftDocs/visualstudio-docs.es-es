---
title: "toUpperCase (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "toUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUpperCase (método)"
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toUpperCase (M&#233;todo, String de JavaScript)
Convierte todos los caracteres alfabéticos de una cadena a caracteres en mayúscula.  
  
## Sintaxis  
  
```  
  
        strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## Comentarios  
 El método `toUpperCase`no tiene efecto en caracteres no alfabéticos.  
  
## Ejemplo  
 En el siguiente ejemplo se muestran los efectos del método `toUpperCase`:  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [toLocaleUpperCase \(Método, String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase \(Método\)](../../javascript/reference/tolowercase-method-javascript.md)