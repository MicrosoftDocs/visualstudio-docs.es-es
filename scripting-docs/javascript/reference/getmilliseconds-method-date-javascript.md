---
title: "getMilliseconds (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "milisegundos"
  - "getMilliseconds (método)"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMilliseconds (M&#233;todo, Date de JavaScript)
Obtiene los milisegundos de un fecha usando la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### Parámetros  
 La referencia obligatoria `dateObj` es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve los milisegundos de una fecha.  El valor puede variar de 0 a 999.  Si se ha creado una fecha sin especificar los milisegundos, el valor devuelto es 0.  
  
## Comentarios  
 Para obtener el número de milisegundos utilizando la hora universal coordinada \(UTC\), usa el método `getUTCMilliseconds`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar el método **getMilliseconds**.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getUTCMilliseconds \(Método, Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds \(Método, Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds \(Método, Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)