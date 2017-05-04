---
title: "getTimezoneOffset (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset (método)"
  - "zonas horarias [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getTimezoneOffset (M&#233;todo, Date de JavaScript)
Obtiene la diferencia en minutos entre la hora del equipo local y el valor de UTC \(Horario universal coordinado\).  
  
## Sintaxis  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve el número de minutos entre la hora del equipo actual \(el equipo cliente o, si se llama a este método desde un script de servidor, el equipo servidor\) y el valor de UTC.  Es positivo si la hora local del equipo actual es posterior al valor de UTC \(por ejemplo, Hora de verano del Pacífico\) y negativo si es anterior al valor de UTC \(por ejemplo, Japón\).  Si un cliente de Los Ángeles se pone en contacto con un servidor ubicado en la ciudad de Nueva York el 1 de diciembre, `getTimezoneOffset` devuelve 480 si se ejecuta en el cliente o 300 si se ejecuta en el servidor.  
  
## Comentarios  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getTimezoneOffset`.  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getTime \(Método, Date\)](../../javascript/reference/gettime-method-date-javascript.md)