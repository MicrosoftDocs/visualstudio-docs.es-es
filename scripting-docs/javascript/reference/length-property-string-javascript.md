---
title: "length (Propiedad, String de JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "cadenas [Visual Studio], longitud"
  - "Length (propiedad)"
  - "length (propiedad, String)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# length (Propiedad, String de JavaScript)
Devuelve la longitud de un objeto `String`.  
  
> [!WARNING]
>  Las cadenas de JavaScript son inmutables, por lo que la longitud de una cadena no se puede modificar.  
  
## Sintaxis  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## Comentarios  
 La propiedad `length` contiene un entero que indica el número de caracteres del objeto `String`.  El último carácter del objeto `String` tiene un índice de i`length` \- 1.  
  
## Ejemplo  
 En el siguiente código se muestra cómo usar `length`.  Las cadenas de JavaScript son inmutables y no se pueden modificar en contexto.  Sin embargo, puedes escribir la cadena invertida en una matriz y llamar después a `join` con el carácter vacío, lo que genera una cadena sin caracteres separadores.  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]