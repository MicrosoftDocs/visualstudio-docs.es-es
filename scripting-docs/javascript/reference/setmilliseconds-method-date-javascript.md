---
title: "setMilliseconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "milisegundos"
  - "setMilliseconds (método)"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMilliseconds (M&#233;todo, Date de JavaScript)
Establece el valor de milisegundos del objeto `Date` que usa la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numMilli`  
 Obligatorio.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Para establecer el valor de milisegundos usando el horario universal coordinado \(UTC\), usa el método `setUTCMilliseconds`.  
  
 Si el valor de `numMilli` es mayor que 999 o es un número negativo, el número almacenado de segundos \(y minutos, horas, etc. según sea necesario\) se incrementa en la cantidad apropiada.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setMilliseconds`.  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMilliseconds \(Método, Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds \(Método, Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds \(Método, Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)