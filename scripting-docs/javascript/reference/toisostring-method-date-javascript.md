---
title: "toISOString (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toISOString (método) [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# toISOString (M&#233;todo, Date de JavaScript)
Devuelve una fecha como un valor alfanumérico en formato ISO.  
  
## Sintaxis  
  
```javascript  
  
objDate.toISOString()  
```  
  
## Valor devuelto  
 Representación de cadena de la fecha en el formato de Organización internacional de normalización \(ISO\).  
  
## Excepciones  
 Si `objDate` no contiene una fecha válida, se produce una excepción `RangeError`.  
  
## Comentarios  
 El formato ISO es una simplificación del formato ISO 8601.  Para obtener más información, consulta [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md).  
  
 La zona horaria siempre es UTC, lo que se indica por el sufijo Z en la salida.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toISOString`.  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)   
 [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md)