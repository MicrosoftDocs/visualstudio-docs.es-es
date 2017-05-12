---
title: "valueOf (M&#233;todo, Error) | Microsoft Docs"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf (M&#233;todo, Error)
Devuelve el valor alfanumérico de un error.  
  
## Sintaxis  
  
```  
  
error.valueOf()  
```  
  
#### Parámetros  
 El objeto `error` es cualquier instancia de un objeto Error.  
  
## Valor devuelto  
 La cadena "Error:” más el mensaje de error.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `valueOF` con una fecha.  
  
```javascript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]