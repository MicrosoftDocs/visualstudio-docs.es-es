---
title: "getTime (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime (método)"
  - "time (método)"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getTime (M&#233;todo, Date de JavaScript)
Obtiene el valor de hora en milisegundos.  
  
## Sintaxis  
  
```  
  
dateObj.getTime()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve el número de milisegundos transcurridos entre la medianoche del 1 de enero de 1970 y el valor de hora del objeto `Date`.  El intervalo de fechas es, aproximadamente, 285.616 años antes o después de la medianoche del 1 de enero de 1970.  Los números negativos indican fechas anteriores a 1970.  
  
## Comentarios  
 Si se hacen varios cálculos de fechas y horas, es posible que desees definir variables iguales al número de milisegundos de un día, hora o minuto.  Por ejemplo:  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Consulta [Calcular fechas y horas \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md) para obtener más información sobre cómo usar el método `getTime`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getTime`.  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [setTime \(Método, Date\)](../../javascript/reference/settime-method-date-javascript.md)