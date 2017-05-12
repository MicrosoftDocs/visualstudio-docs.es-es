---
title: "getUTCDay (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "fechas, UTC"
  - "Fechas UTC, devolver"
  - "getUTCDay (método)"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getUTCDay (M&#233;todo, Date de JavaScript)
Obtiene el día de la semana utilizando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve un entero comprendido entre 0 \(domingo\) y 6 \(sábado\) que representa el día de la semana.  
  
## Comentarios  
 Para obtener el día de la semana utilizando la hora local, usa el método `getDate`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getUTCDay`.  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getDay \(Método, Date\)](../../javascript/reference/getday-method-date-javascript.md)