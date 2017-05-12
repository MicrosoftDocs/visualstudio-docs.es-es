---
title: "Funci&#243;n String.fromCodePoint (JavaScript) | Microsoft Docs"
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
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funci&#243;n String.fromCodePoint (JavaScript)
Devuelve la cadena asociada a un punto de código Unicode UTF\-16.  
  
## Sintaxis  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### Parámetros  
 `…codePoints`  
 Requerido.  Un parámetro de rest que especifica uno o varios valores de punto de código UTF\-16.  
  
## Comentarios  
 Esta función genera una excepción `RangeError` si `...codePoints` no es un punto de código UTF\-16 válido.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar la función `fromCodePoint`.  
  
```javascript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]