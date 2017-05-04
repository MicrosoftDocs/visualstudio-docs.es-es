---
title: "format (Propiedad, Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format (Propiedad, Intl.DateTimeFormat)
Devuelve una función que da formato a una fecha específica de la configuración regional mediante la configuración del formateador de fecha y hora especificada.  
  
## Sintaxis  
  
```  
dateTimeFormatObj.format  
```  
  
#### Parámetros  
 `dateTimeFormatObj`  
 Requerido.  El nombre del objeto `DateTimeFormat` que se va a usar como formateador.  
  
## Comentarios  
 La función devuelta por la propiedad `format` toma un único argumento, `date`, y devuelve una cadena que representa la fecha localizada utilizando las opciones especificadas en el objeto `DateTimeFormat`.  El parámetro `date` de la función devuelta debe ser un número, una cadena de fecha o un objeto `Date`.  Si no se proporciona `date`, la función utiliza [Date.now](../../javascript/reference/date-now-function-javascript.md) como valor predeterminado de entrada.  
  
## Ejemplo  
 El ejemplo siguiente usa un objeto `DateTimeFormat` para localizar la fecha “1 de diciembre de 2007” en alemán y para cambiarle el formato.  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [Intl.DateTimeFormat \(Objeto\)](../../javascript/reference/intl-datetimeformat-object-javascript.md)