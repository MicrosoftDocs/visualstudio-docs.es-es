---
title: "toLocaleString (M&#233;todo, Object de JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString (método)"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toLocaleString (M&#233;todo, Object de JavaScript)
Devuelve una fecha convertida en cadena utilizando la configuración regional actual.  
  
## Sintaxis  
  
```  
  
dateObj.toLocaleString()   
```  
  
## Comentarios  
 El parámetro `dateObj` obligatorio es cualquier objeto `Date`.  
  
 El método `toLocaleString` devuelve un objeto `String` que contiene la fecha escrita en el formato largo predeterminado de la configuración regional actual.  
  
-   Para fechas comprendidas entre 1601 y 1999 d. C., se aplica formato a la fecha de acuerdo con la configuración regional del Panel de control del usuario.  
  
-   Para fechas no incluidas dentro de este intervalo, se utiliza el formato predeterminado del método **toString**.  
  
 Por ejemplo, en los Estados Unidos, `toLocaleString` devuelve "01\/05\/96 00:00:00" para el 5 de enero.  En Europa, devuelve "05\/01\/96 00:00:00" para la misma fecha, puesto que la convención europea coloca el día antes del mes.  
  
> [!NOTE]
>  El método `toLocaleString` únicamente debe utilizarse para mostrar resultados al usuario; no debe utilizarse nunca como base para procesar datos dentro de un script, ya que el resultado devuelto depende del equipo.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)&#124; [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)&#124; [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)&#124; [Object \(Objeto\)](../../javascript/reference/object-object-javascript.md)  
  
## Vea también  
 [toLocaleDateString \(Método, Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)