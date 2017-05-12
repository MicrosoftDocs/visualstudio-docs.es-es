---
title: "toUTCString (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString (método)"
  - "fechas UTC, convertir a cadenas"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toUTCString (M&#233;todo, Date de JavaScript)
Devuelve una fecha convertida en cadena usando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.toUTCString()   
```  
  
## Comentarios  
 La referencia obligatoria `dateObj` es cualquier objeto `Date`.  
  
 El método `toUTCString` devuelve un objeto `String` que contiene la fecha con el formato propio de la convención UTC en un formato práctico de fácil lectura.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toUTCString`.  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [toGMTString \(Método, Date\)](../../javascript/reference/togmtstring-method-date-javascript.md)