---
title: "setUTCFullYear (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "setUTCFullYear (método)"
  - "fechas UTC, establecer"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCFullYear (M&#233;todo, Date de JavaScript)
Establece el valor de año del objeto `Date` usando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numYear`  
 Obligatorio.  Valor numérico igual al año.  
  
 `numMonth`  
 Opcional.  Valor numérico igual al mes.  El valor correspondiente a enero es 0 y los valores de los demás meses son los siguientes de forma consecutiva.  Se debe proporcionar si se proporciona el argumento *numDate*.  
  
 *numDate*  
 Opcional.  Valor numérico que equivale al día del mes.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento `numMonth`, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método `getUTCMonth`.  
  
 Además, si el valor de un argumento es mayor que su intervalo o es un número negativo, otros valores almacenados se modifican en consecuencia.  
  
 Para establecer el año mediante la hora local, usa el método `setFullYear`.  
  
 El intervalo de años admitido en el objeto `Date` es aproximadamente 285.616 años antes o después de 1970.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCFullYear`.  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getFullYear \(Método, Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear \(Método, Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)