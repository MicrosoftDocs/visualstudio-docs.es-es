---
title: "Intervalo no v&#225;lido en el juego de caracteres (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Intervalo no v&#225;lido en el juego de caracteres (JavaScript)
Has intentado crear una expresión regular con un intervalo no válido de juegos de caracteres.  Los juegos de caracteres deben ir desde caracteres individuales únicamente, como a\-z o 0\-9; no puedes incluir clases de caracteres como \\w en un juego de caracteres.  El primer carácter del intervalo también debe figurar delante del segundo carácter del intervalo.  Por ejemplo:  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### Para corregir este error  
  
-   Usa solo caracteres individuales para componer el juego de caracteres de la expresión regular y asegúrate de que están en el orden correcto.  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)