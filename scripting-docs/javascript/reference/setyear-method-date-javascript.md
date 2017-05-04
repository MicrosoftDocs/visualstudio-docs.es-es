---
title: "setYear (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear (método)"
  - "Year (método)"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# setYear (M&#233;todo, Date de JavaScript)
Establece el valor de año del objeto `Date`.  
  
## Sintaxis  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numYear`  
 Obligatorio.  Para los años comprendidos entre 1900 y 1999, es un valor numérico igual al año menos 1900.  Para las fechas fuera de ese intervalo, es un valor numérico de 4 dígitos.  
  
## Comentarios  
 Este método está obsoleto y solo se mantiene por compatibilidad con versiones anteriores.  Usa el método `setFullYear` en su lugar.  
  
 Para establecer el año de un objeto `Date` en 1997, llama al método **setYear\(97\)**.  Para establecer el año en 2010, llama al método **setYear\(2010\)**.  Finalmente, para establecer el año en un año del intervalo comprendido entre 0 y 99, usa el método `setFullYear`.  
  
> [!NOTE]
>  En [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] versión 1.0, el método `setYear` usa un valor que es el resultado de sumar a 1900 el valor de año proporcionado por `numYear`, con independencia del valor del año.  Por ejemplo, para establecer el año 1899, `numYear` es \-1 y para establecer el año 2000, `numYear` es 100.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getFullYear \(Método, Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear \(Método, Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear \(Método, Date\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear \(Método, Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)