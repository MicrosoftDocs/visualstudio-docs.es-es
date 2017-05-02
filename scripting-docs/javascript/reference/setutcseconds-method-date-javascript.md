---
title: "setUTCSeconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "seconds (método)"
  - "setUTCSeconds (método)"
  - "horas UTC, establecer"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCSeconds (M&#233;todo, Date de JavaScript)
Establece el valor de segundos del objeto `Date` usando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 *numSeconds*  
 Obligatorio.  Valor numérico igual al valor de los segundos.  
  
 `numMilli`  
 Opcional.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento `numMilli`, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método `getUTCMilliseconds`.  
  
 Para establecer el valor de segundos mediante la hora local, usa el método `setSeconds`.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de a las 1996 00:00:00.00 y se llama a **setSeconds\(150\)**, la fecha cambia al 5 de enero de 1996 a las 00:02:30.00.  
  
 Se puede usar el método **setUTCHours** para establecer las horas, los minutos, los segundos y los milisegundos.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCSeconds`.  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getSeconds \(Método, Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds \(Método, Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds \(Método, Date\)](../../javascript/reference/setseconds-method-date-javascript.md)