---
title: "toLowerCase (M&#233;todo de JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase (método)"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLowerCase (M&#233;todo de JavaScript)
Convierte todos los caracteres alfabéticos de una cadena a caracteres en minúscula.  
  
## Sintaxis  
  
```  
  
        strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## Comentarios  
 El método `toLowerCase`no tiene efecto en caracteres no alfabéticos.  
  
 En el siguiente ejemplo se muestran los efectos del método `toLowerCase`:  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [toLocaleLowerCase \(Método, String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase \(Método, String\)](../../javascript/reference/touppercase-method-string-javascript.md)