---
title: "setUTCMilliseconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, UTC"
  - "milisegundos"
  - "setUTCMilliseconds (método)"
  - "horas UTC, establecer"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMilliseconds (M&#233;todo, Date de JavaScript)
Establece el valor de milisegundos del objeto `Date` usando el horario universal coordinado \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numMilli`  
 Obligatorio.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Para establecer el valor de milisegundos mediante la hora local, usa el método `setMilliseconds`.  
  
 Si el valor de `numMilli` es mayor que 999, o es un número negativo, el número almacenado de segundos \(y minutos, horas, etc. según sea necesario\) se incrementa en la cantidad apropiada.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setUTCMilliseconds`.  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMilliseconds \(Método, Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds \(Método, Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds \(Método, Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)