---
title: "toString (M&#233;todo, Error) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString (M&#233;todo, Error)
Devuelve una representación alfanumérica de un error.  
  
## Sintaxis  
  
```  
  
error.toString()  
```  
  
## Parámetros  
 `date`  
 Obligatorio.  Error que se va a representar de forma alfanumérica.  
  
## Valor devuelto  
 Devuelve "Error: ” más el mensaje de error.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toString` con un error.  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]