---
title: "getDay (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay (método)"
  - "Date (objeto)"
  - "fechas, devolver día de la semana"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# getDay (M&#233;todo, Date de JavaScript)
Obtiene el día de la semana usando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj. getDay()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Un entero entre 0 y 6 que representa el día de la semana \(domingo es 0 y sábado es 6\).  
  
## Comentarios  
 Para obtener el día utilizando la hora universal coordinada \(UTC\), usa el método `getUTCDay`.  
  
 En el siguiente ejemplo, se muestra cómo usar el método `getDay`.  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCDay \(Método, Date\)](../../javascript/reference/getutcday-method-date-javascript.md)