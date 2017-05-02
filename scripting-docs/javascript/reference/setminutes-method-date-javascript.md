---
title: "setMinutes (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "minutos"
  - "setMinutes (método)"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMinutes (M&#233;todo, Date de JavaScript)
Establece el valor de minutos del objeto **Date** que usa la hora local.  
  
## Sintaxis  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Parámetros  
 `dateObj`  
 Obligatorio.  Cualquier objeto `Date`.  
  
 `numMinutes`  
 Obligatorio.  Valor numérico igual al valor de los minutos.  Se debe proporcionar si se usa cualquiera de los argumentos siguientes.  
  
 *numSeconds*  
 Opcional.  Valor numérico igual al valor de los segundos.  Se debe proporcionar si se usa el argumento `numMilli`.  
  
 `numMilli`  
 Opcional.  Valor numérico igual al valor de milisegundos.  
  
## Comentarios  
 Si no especificas un argumento opcional, todos los métodos **set** que toman argumentos opcionales usan el valor devuelto por los métodos **get** correspondientes.  Por ejemplo, si no se especifica el argumento *numSeconds*, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa el valor devuelto por el método `getSeconds`.  
  
 Para establecer el valor de minutos usando el horario universal coordinado \(UTC\), usa el método `setUTCMinutes`.  
  
 Si el valor de un argumento es mayor que su intervalo o es un número negativo, los demás valores almacenados se modifican en consecuencia.  Por ejemplo, si la fecha almacenada es el 5 de enero de 1996 a las 00:00:00 y se llama a **setMinutes\(90\)**, la fecha cambia al 5 de enero de 1996 a las 01:30:00. Los números negativos tienen un comportamiento similar.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `setMinutes`.  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getMinutes \(Método, Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes \(Método, Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes \(Método, Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)