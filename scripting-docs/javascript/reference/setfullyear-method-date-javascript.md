---
title: "setFullYear (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year (método)"
  - "setFullYear (método)"
  - "fechas, configuración"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setFullYear (M&#233;todo, Date de JavaScript)
Establece el año del objeto de `Date` date.  
  
## Sintaxis  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numYear`  
 Obligatorio.  Un valor numérico del año.  
  
 `numMonth`  
 Opcional.  Un valor numérico cero\- dependiendo del mes \(0 de enero, 11 para diciembre\).  Se debe especificar si se especifica `numDate` .  
  
 `numDate`  
 Opcional.  Un valor numérico igual para el día del mes.  
  
## Comentarios  
 Si no se especifica el argumento opcional, todos los métodos **set** que toman argumentos opcionales utilizan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si el argumento de `numMonth` es opcional, pero no especificado, de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] el valor devuelto del método de **getMonth** .  
  
 Además, si el valor de un argumento es mayor que el intervalo del calendario o es negativo, las operaciones de puesta al día de la fecha o retroceder según corresponda.  
  
 Para establecer el año utilizando la hora Universal coordinada \(hora UTC\), utilice el método de `setUTCFullYear` .  
  
 El intervalo de acción de años admitidos en el objeto date es aproximadamente 285.616 años antes y después de 1970.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso del método `setFullYear`:  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getFullYear \(Método, Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear \(Método, Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear \(Método, Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)