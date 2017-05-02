---
title: "toTimeString (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString (método)"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toTimeString (M&#233;todo, Date de JavaScript)
Devuelve una hora como un valor alfanumérico.  
  
## Sintaxis  
  
```  
  
objDate. toTimeString( )  
```  
  
## Comentarios  
 La referencia obligatoria `objDate` es un objeto `Date`.  
  
 El método `toTimeString` devuelve un valor alfanumérico que contiene la hora en la zona horaria actual.  
  
## Ejemplo  
 En el ejemplo siguiente, se establece la hora en 2000 milisegundos después de la medianoche del 1 de enero de 1970 UTC y después se escribe.  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [toDateString \(Método, Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString \(Método, Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)