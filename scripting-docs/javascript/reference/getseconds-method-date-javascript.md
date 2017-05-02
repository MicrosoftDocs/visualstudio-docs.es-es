---
title: "getSeconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds (método)"
  - "GetSeconds (método)"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getSeconds (M&#233;todo, Date de JavaScript)
Obtiene los segundos de un objeto de `Date` , date.  
  
## Sintaxis  
  
```  
  
dateObj.getSeconds()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve un entero entre 0 y 59.  Se devuelve cero cuando el tiempo es menos de segundo del minuto actual.  Si un objeto de `Date` se creó sin especificar el tiempo, de forma predeterminada el valor de los segundos es 0.  
  
## Comentarios  
 Para obtener el valor de los segundos utilizando la hora Universal coordinada \(hora UTC\), utilice el método de `getUTCSeconds` .  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCSeconds \(Método, Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds \(Método, Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds \(Método, Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)