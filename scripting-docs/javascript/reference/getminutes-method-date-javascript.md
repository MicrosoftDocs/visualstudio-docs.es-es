---
title: "getMinutes (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes (método)"
  - "minutes (método)"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMinutes (M&#233;todo, Date de JavaScript)
Obtiene los minutos de un objeto `Date` utilizando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.getMinutes()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve un entero entre 0 y 59.  Se devuelve cero cuando el tiempo es inferior a un minuto después de la hora.  Si se ha creado un objeto `Date` sin especificar la hora, el valor de los minutos es 0 de forma predeterminada.  
  
## Comentarios  
 Para obtener el valor de minutos usando el horario universal coordinado \(UTC\), usa el método `getUTCMinutes`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar el método `getMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCMinutes \(Método, Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes \(Método, Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes \(Método, Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)