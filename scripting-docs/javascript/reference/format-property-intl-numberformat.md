---
title: "format (Propiedad, Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format (Propiedad, Intl.NumberFormat)
Devuelve una función que da formato a un número específico de la configuración regional mediante la configuración del formateador de número especificada.  
  
## Sintaxis  
  
```  
numberFormatObj.format  
```  
  
#### Parámetros  
 `numberFormatObj`  
 Requerido.  El nombre del objeto `NumberFormat` que se va a usar como formateador.  
  
## Comentarios  
 La función devuelta por la propiedad `format` toma un único argumento, `value`, y devuelve una cadena que representa el número localizado utilizando las opciones especificadas en el objeto `NumberFormat`.  Si no se proporciona `value`, la función devuelve `NaN` \(no es un número\).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza un objeto `NumberFormat` para crear un número localizado.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [Intl.NumberFormat \(Objeto\)](../../javascript/reference/intl-numberformat-object-javascript.md)