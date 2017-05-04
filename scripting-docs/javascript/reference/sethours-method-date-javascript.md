---
title: "setHours (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, establecer"
  - "horas"
  - "setHours (método)"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setHours (M&#233;todo, Date de JavaScript)
Establece el valor de hora del objeto `Date` que usa la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numHours`  
 Obligatorio.  Valor numérico igual al valor de las horas.  
  
 `numMin`  
 Opcional.  Valor numérico igual al valor de los minutos.  Se debe proporcionar si se usa cualquiera de los argumentos siguientes.  
  
 `numSec`  
 Opcional.  Valor numérico igual al valor de los segundos.  Se debe proporcionar si se usa el argumento siguiente.  
  
 `numMilli`  
 Opcional.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento `numMinutes`, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método `getMinutes`.  
  
 Para establecer el valor de horas usando el horario universal coordinado \(UTC\), usa el método `setUTCHours`.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 a las 00:00:00 y se llama a **setHours\(30\)**, la fecha cambia al 6 de enero de 1996 a las 06:00:00. Los números negativos tienen un comportamiento similar.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setHours`.  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getHours \(Método, Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours \(Método, Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours \(Método, Date\)](../../javascript/reference/setutchours-method-date-javascript.md)