---
title: "getDate (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "fechas, devolver día del mes"
  - "getDate (método)"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# getDate (M&#233;todo, Date de JavaScript)
Obtiene el día del mes usando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.getDate()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Un entero entre 1 y 31 que representa el día del mes.  
  
## Comentarios  
 Para obtener el día del mes usando el horario universal coordinado \(UTC\), debes utilizar el método `getUTCDate`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getDate`.  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCDate \(Método, Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate \(Método, Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate \(Método, Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)