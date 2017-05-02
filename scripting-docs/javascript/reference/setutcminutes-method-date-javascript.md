---
title: "setUTCMinutes (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "minutos"
  - "setUTCMinutes (método)"
  - "horas UTC, establecer"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMinutes (M&#233;todo, Date de JavaScript)
Establece, utilizando la hora universal coordinada \(UTC\), el valor de minutos del objeto `Date`.  
  
## Sintaxis  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numMinutes`  
 Obligatorio.  Valor numérico igual al valor de los minutos.  Se debe proporcionar si se usa cualquiera de los argumentos siguientes.  
  
 *numSeconds*  
 Opcional.  Valor numérico igual al valor de los segundos.  Se debe proporcionar si se utiliza `numMilli`.  
  
 `numMilli`  
 Opcional.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento *numSeconds*, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método `getUTCSeconds`.  
  
 Para modificar el valor de los minutos utilizando la hora local, usa el método `setMinutes`.  
  
 Si el valor de un argumento es mayor que su intervalo, o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 a las 00:00:00.00 y se llama a **setUTCMinutes\(70\)**, la fecha cambia al 5 de enero de 1996 a la 01:10:00.00.  
  
 Se puede usar el método **setUTCHours** para establecer las horas, los minutos, los segundos y los milisegundos.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCMinutes`:  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMinutes \(Método, Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes \(Método, Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes \(Método, Date\)](../../javascript/reference/setminutes-method-date-javascript.md)