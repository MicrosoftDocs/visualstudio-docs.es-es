---
title: "M&#233;todo includes (cadena) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo includes (cadena) (JavaScript)
Devuelve un valor booleano que indica si la cadena pasada se encuentra en el objeto de cadena.  
  
## Sintaxis  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### Parámetros  
 `stringObj`  
 Obligatorio.  Objeto de cadena con el que se va a probar.  
  
 `substring`  
 Obligatorio.  Cadena que se va a comprobar.  
  
 `position`  
 Opcional.  La posición del primer carácter con el que se va a probar en el objeto de cadena, empezando por 0.  
  
## Valor devuelto  
 Si la cadena pasada se encuentra en el objeto de cadena, el método `includes` devuelve `true`; en caso contrario, devuelve `false`.  
  
## Comentarios  
  
## Ejemplo  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]