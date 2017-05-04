---
title: "getUTCMinutes (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "minutos"
  - "horas UTC, devolver"
  - "getUTCMinutes (método)"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMinutes (M&#233;todo, Date de JavaScript)
Obtiene el valor de un objeto de `Date` utilizando la hora Universal coordinada \(hora UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve un entero entre 0 y 59.  Cero se devuelve la hora es menos de un minuto después de la hora.  Si un objeto de `Date` se creó sin especificar el tiempo, de forma predeterminada el valor de mínimo UTC es 0.  Sin embargo, en otras zonas horarias puede ser diferente.  
  
## Comentarios  
 Para obtener el número de minutos almacenados mediante la hora local, utilice el método `getMinutes`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `getUTCMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMinutes \(Método, Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes \(Método, Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes \(Método, Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)