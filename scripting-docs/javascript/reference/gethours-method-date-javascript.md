---
title: "getHours (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "GetHours (método)"
  - "Hours (método)"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getHours (M&#233;todo, Date de JavaScript)
Obtiene las horas de una fecha, usando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.getHours()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Un entero entre 0 y 23 que indica el número de horas transcurrido desde la medianoche.  Se devuelve cero si la hora es anterior a la 1:00:00 a.m.  Si se ha creado un objeto `Date` sin especificar la hora, la hora es 0 de forma predeterminada.  
  
## Comentarios  
 Para obtener el valor de horas usando el horario universal coordinado \(UTC\), usa el método `getUTCHours`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCHours \(Método, Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours \(Método, Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours \(Método, Date\)](../../javascript/reference/setutchours-method-date-javascript.md)