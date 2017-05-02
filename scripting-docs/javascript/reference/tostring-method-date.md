---
title: "toString (M&#233;todo, Date) | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString (M&#233;todo, Date)
Devuelve una representación de cadena de una fecha.  El formato de la cadena depende de la configuración regional.  Para inglés de EE..UU.. \(en\-us\), es la siguiente:  
  
 *día de la semana* *mes* *día* *hora*: *minuto*:*segundo* *zona horaria* *año*  
  
## Sintaxis  
  
```  
  
date.toString()  
```  
  
## Parámetros  
 `date`  
 Requerido.  Fecha que se va a representar como una cadena.  
  
## Valor devuelto  
 Devuelve la representación de cadena de la fecha.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toString` con una fecha.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]