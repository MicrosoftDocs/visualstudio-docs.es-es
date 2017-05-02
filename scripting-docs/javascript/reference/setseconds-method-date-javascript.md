---
title: "setSeconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds (método)"
  - "setSeconds (método)"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setSeconds (M&#233;todo, Date de JavaScript)
Establece el valor de segundos del objeto `Date` que usa la hora local.  
  
## Sintaxis  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 *numSeconds*  
 Obligatorio.  Valor numérico igual al valor de los segundos.  
  
 `numMilli`  
 Opcional.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento `numMilli`, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método **getMilliseconds**.  
  
 Para establecer el valor de segundos usando el horario universal coordinado \(UTC\), usa el método `setUTCSeconds`.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 a las 00:00:00" y se llama a **setSeconds\(150\)**, la fecha cambia al 5 de enero de 1996 a las 00:02:30.  
  
 Se puede usar el método `setHours` para establecer las horas, los minutos, los segundos y los milisegundos.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setSeconds`.  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getSeconds \(Método, Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds \(Método, Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds \(Método, Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)