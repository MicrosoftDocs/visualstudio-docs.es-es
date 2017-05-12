---
title: "Excepci&#243;n producida y no detectada | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Excepci&#243;n producida y no detectada
Has incluido una instrucción `throw` en el código, pero no estaba dentro de un bloque **try** o no había ningún bloque **catch** asociado para interceptar el error.  Las excepciones se producen dentro del bloque **try** mediante la instrucción **throw** y se detectan fuera del bloque **try** con una instrucción **catch**.  
  
### Para corregir este error  
  
-   Pon en un bloque **try** el código que puede producir una excepción y asegúrate de que haya un bloque **catch** correspondiente.  
  
-   Asegúrate de que la instrucción catch espera el formato correcto de excepción.  
  
-   Si se vuelve a producir la excepción, asegúrate de que haya otra instrucción catch correspondiente.  
  
## Vea también  
 [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)   
 [throw \(Instrucción\)](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally \(Instrucción\)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)