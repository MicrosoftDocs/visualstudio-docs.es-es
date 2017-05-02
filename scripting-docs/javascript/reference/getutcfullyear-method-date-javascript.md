---
title: "getUTCFullYear (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear (Método)"
  - "Date (objeto)"
  - "UTCFullYear (Método)"
  - "fechas, UTC"
  - "fechas UTC, devolver"
  - "Full Year (método)"
  - "fechas UTC, obtener"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCFullYear (M&#233;todo, Date de JavaScript)
Obtiene el año utilizando el horario universal coordinada \(UTC\).  
  
## Sintaxis  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve el año como un número de cuatro dígitos.  Se supone que los años especificados como dos dígitos en el constructor `Date` o en `setFullYear` pertenecen al siglo XX, por lo que si se da “5\/14\/12", `getUTCFullYear` devuelve “1912”.  
  
## Comentarios  
 Para obtener el año mediante la hora local, usa el método `getFullYear`.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo usar el método `getUTCFullYear`.  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getFullYear \(Método, Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear \(Método, Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)