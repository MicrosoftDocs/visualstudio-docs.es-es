---
title: "valueOf (M&#233;todo, String) | Microsoft Docs"
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
ms.assetid: dfb55e6b-e38f-4b49-8196-9693f87126a4
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf (M&#233;todo, String)
Devuelve la cadena.  
  
## Sintaxis  
  
```  
  
string.valueOf()  
```  
  
#### Parámetros  
 Este método no tiene parámetros.  
  
## Valor devuelto  
 Devuelve el valor alfanumérico.  
  
## Comentarios  
 En el ejemplo siguiente, el objeto de cadena es igual que el valor devuelto.  
  
```javascript  
var str = "every good boy does fine";  
var strStr = str.valueOf();  
  
if (str === strStr)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]