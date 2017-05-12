---
title: "Throw debe ir seguido de una expresi&#243;n en la misma l&#237;nea de c&#243;digo fuente | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Throw debe ir seguido de una expresi&#243;n en la misma l&#237;nea de c&#243;digo fuente
Has usado la palabra clave `throw`, pero después de ella no hay una expresión en la misma línea de código fuente.  Una instrucción `throw` consta de dos partes: la palabra clave `throw` seguida de la expresión que se va a producir.  Por ejemplo:  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 No puedes dividir estos dos componentes.  
  
### Para corregir este error  
  
-   Asegúrate de que la palabra clave `throw` y la expresión que se producirá aparecen en la misma línea.  
  
## Vea también  
 [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)   
 [throw \(Instrucción\)](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally \(Instrucción\)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)