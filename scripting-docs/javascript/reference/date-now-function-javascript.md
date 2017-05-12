---
title: "Funci&#243;n Date.now (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "now (método)"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Funci&#243;n Date.now (JavaScript)
Obtiene la fecha y hora actuales.  
  
## Sintaxis  
  
```  
  
Date.now()  
```  
  
## Valor devuelto  
 Número de milisegundos que hay entre la medianoche del 1 de enero de 1970 y la fecha y hora actuales.  
  
## Comentarios  
 El [método getTime](../../javascript/reference/gettime-method-date-javascript.md) devuelve el número de milisegundos que hay entre el 1 de enero de 1970 y una fecha especificada.  
  
 Para obtener información acerca de cómo calcular el tiempo transcurrido y comparar fechas, vea [Calcular fechas y horas \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `now`.  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## Requisitos  
 No se admite en las versiones instaladas anteriores a Internet Explorer 9.  Sin embargo, se admite en los siguientes modos de documento: no estándares, estándares de Internet Explorer 6, estándares de Internet Explorer 7, estándares de Internet Explorer 8, estándares de Internet Explorer 9 y estándares de Internet Explorer 10.  También se admiten en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## Vea también  
 [getTime \(Método, Date\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)   
 [Calcular fechas y horas \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)