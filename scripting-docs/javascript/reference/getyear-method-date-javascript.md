---
title: "getYear (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fechas, devolver año"
  - "GetYear (método)"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# getYear (M&#233;todo, Date de JavaScript)
Obtiene el año de un objeto de `Date` .  
  
## Sintaxis  
  
```  
  
dateObj.getYear()   
```  
  
#### Parámetros  
 La referencia requerida de `dateObj` es un objeto de `Date` .  
  
## Valor devuelto  
 Devuelve el año.  
  
## Comentarios  
  
> [!IMPORTANT]
>  Este método está obsoleto, y se proporciona para la compatibilidad con versiones anteriores de.  Utilice el método `getFullYear` en su lugar.  
  
 En [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]y, en las versiones de Internet Explorer que comienzan con [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], el valor devuelto es el año almacenado menos 1900.  Por ejemplo, el año 1899 se devuelve como \-1 y el año 2000 se devuelve como 100.  
  
 En [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] con [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], la fórmula depende del año.  Por los años 1900 hasta el 1999, el valor devuelto es un valor de 2 dígitos que es el año almacenado menos 1900.  Para fuera de las fechas que se extiende, devuelve el año de 4 dígitos.  Por ejemplo, 1996 se devuelve como 96, pero se devuelve 1825 y 2025 como está.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getFullYear \(Método, Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear \(Método, Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear \(Método, Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear \(Método, Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear \(Método, Date\)](../../javascript/reference/setyear-method-date-javascript.md)