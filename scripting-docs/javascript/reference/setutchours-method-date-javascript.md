---
title: "setUTCHours (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "setUTCHours (método)"
  - "horas UTC, establecer"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setUTCHours (M&#233;todo, Date de JavaScript)
Establece, utilizando la hora universal coordinada \(UTC\), el valor de horas del objeto `Date`.  
  
## Sintaxis  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numHours`  
 Obligatorio.  Valor numérico igual al valor de las horas.  
  
 `numMin`  
 Opcional.  Valor numérico igual al valor de los minutos.  Debe proporcionarse si se usa `numSec` o `numMilli`.  
  
 `numSec`  
 Opcional.  Valor numérico igual al valor de los segundos.  Se debe proporcionar si se usa el argumento `numMilli`.  
  
 `numMilli`  
 Opcional.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento `numMin`, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método `getUTCMinutes`.  
  
 Para establecer el valor de las horas utilizando la hora local, usa el método `setHours`.  
  
 Si el valor de un argumento es mayor que su intervalo, o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 a las 00:00:00.00 y se llama a **setUTCHours\(30\)**, la fecha cambia al 6 de enero de 1996 a las 06:00:00.00.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCHours`.  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getHours \(Método, Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours \(Método, Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours \(Método, Date\)](../../javascript/reference/sethours-method-date-javascript.md)