---
title: "getFullYear (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, devolver año"
  - "Date (objeto)"
  - "getFullYear (método)"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# getFullYear (M&#233;todo, Date de JavaScript)
Obtiene el año usando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.getFullYear()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 El año como un número de cuatro dígitos.  Por ejemplo, el año 1976 se devuelve como 1976.  Se supone que los años especificados como dos dígitos en el constructor `Date` o en `setFullYear` pertenecen al siglo XX, por lo que si se da “5\/14\/12", `getFullYear` devuelve “1912”.  
  
## Comentarios  
 Para obtener el año mediante el horario universal coordinado \(UTC\), usa el método `getUTCFullYear`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **getFullYear**.  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCFullYear \(Método, Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear \(Método, Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)