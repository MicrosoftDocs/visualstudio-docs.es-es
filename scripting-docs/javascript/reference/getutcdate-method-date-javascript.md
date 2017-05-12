---
title: "getUTCDate (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "fechas, UTC"
  - "fechas UTC, devolver"
  - "getUTCDate (método)"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getUTCDate (M&#233;todo, Date de JavaScript)
Obtiene el día del mes utilizando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve un entero entre 1 y 31 que representa el día del mes.  
  
## Comentarios  
 Para obtener el día del mes usando la hora local, usa el método `getDate`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getUTCDate`.  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getDate \(Método, Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate \(Método, Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate \(Método, Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)