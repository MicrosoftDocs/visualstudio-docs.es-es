---
title: "setTime (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime (método)"
  - "time (método)"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# setTime (M&#233;todo, Date de JavaScript)
Establece el valor de fecha y hora en el objeto `Date`.  
  
## Sintaxis  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 *milliseconds*  
 Obligatorio.  Valor numérico que representa el número de milisegundos transcurridos desde la medianoche del 1 de enero de 1970 GMT.  
  
## Comentarios  
 Si *milliseconds* es negativo, indica una fecha anterior a 1970.  El intervalo de fechas disponibles es de aproximadamente 285.616 años a partir de 1970 en cualquier dirección.  
  
 La acción de establecer la fecha y la hora con el método `setTime` es independiente de la zona horaria.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setTime`.  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getTime \(Método, Date\)](../../javascript/reference/gettime-method-date-javascript.md)