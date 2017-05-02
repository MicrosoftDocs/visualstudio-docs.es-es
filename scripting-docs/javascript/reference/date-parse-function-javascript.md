---
title: "Date.parse (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse (función) [JavaScript]"
  - "parse (función) [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Date.parse (Funci&#243;n de JavaScript)
Analiza una cadena que contiene una fecha y devuelve el número de milisegundos transcurridos entre esa fecha y la medianoche del 1 de enero de 1970.  
  
## Sintaxis  
  
```  
Date.parse(dateVal)   
```  
  
## Comentarios  
 El argumento obligatorio `dateVal` es una cadena que contiene una fecha o un valor VT\_DATE recuperado de un objeto ActiveX u otro objeto.  Para obtener información acerca de las cadenas de fecha que la función `Date.parse` puede analizar, vea [Cadenas de fecha y hora](../../javascript/date-and-time-strings-javascript.md).  
  
 La función `Date.parse` devuelve un valor entero que representa el número de milisegundos transcurridos entre la medianoche del 1 de enero de 1970 y la fecha proporcionada en el argumento `dateVal`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Date.parse`.  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## Ejemplo  
 En el ejemplo siguiente se devuelve la diferencia entre la fecha proporcionada y 1\/1\/1970.  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [getDate \(Método, Date\)](../../javascript/reference/getdate-method-date-javascript.md)