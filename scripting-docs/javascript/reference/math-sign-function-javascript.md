---
title: "Funci&#243;n Math.sign (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n Math.sign (JavaScript)
Devuelve el signo de un número, que indica si el número es positivo, negativo o 0.  
  
## Sintaxis  
  
```  
Math.sign(number)  
```  
  
## Comentarios  
 El argumento `number` obligatorio es una expresión numérica para la que se necesita el signo.  
  
 El valor devuelto es uno de los siguientes:  
  
-   `NaN`, si `number` es `NaN`.  
  
-   \-0, si `number` es \-0.  
  
-   \+0, si `number` es \+0.  
  
-   \-1, si `number` es negativo y no \-0.  
  
-   \+1, si `number` es positivo y no \+0.  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]