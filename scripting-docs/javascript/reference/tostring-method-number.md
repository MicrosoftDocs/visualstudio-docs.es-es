---
title: "toString (M&#233;todo, Number) | Microsoft Docs"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString (M&#233;todo, Number)
Devuelve una representación alfanumérica de un número.  
  
## Sintaxis  
  
```  
  
number.toString()  
```  
  
## Parámetros  
 `number`  
 Obligatorio.  Número que se va a representar de forma alfanumérica.  
  
## Valor devuelto  
 Representación alfanumérica del número.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **toString** con un número.  
  
```javascript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]