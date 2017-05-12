---
title: "toLocaleDateString (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString (método)"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLocaleDateString (M&#233;todo, Date de JavaScript)
Devuelve una fecha como un valor de cadena apropiado para la configuración regional actual del entorno host o la configuración regional especificada.  
  
## Sintaxis  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### Parámetros  
 `dateObj`  
 Requerido.  Un objeto `Date`.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de la configuración regional, enumérelas en orden descendente de prioridad para de manera que la primera entrada se la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional.  Un objeto que contiene una o más propiedades que especifican opciones de comparación.  
  
## Comentarios  
 A partir de Internet Explorer 11, `toLocaleDateString` utiliza el objeto `Intl.DateTimeFormat` internamente para formatear la fecha, lo que agrega compatibilidad para los parámetros `locales` y `options`.  Para obtener más información sobre estos parámetros, vea [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento y versiones de explorador.  Para obtener más información, consulte la sección Requisitos.  
  
 Cuando usa `toLocaleDateString` en modo "quirks", en modo de documento anterior y en modo de documento estándar de Internet Explorer 10:  
  
-   devuelve un valor de cadena que contiene una fecha en la zona horaria actual.  
  
-   La fecha devuelta tiene el formato predeterminado de la configuración regional actual del entorno host.  
  
 Si omite el parámetro `locales`, el valor devuelto por este método no se puede basar en el scripting, ya que variará entre equipos.  En este escenario, utilice el método solo para dar formato al texto mostrado \(nunca como parte de un cálculo\).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleDateString` con opciones de configuración regional y comparación especificadas.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Los parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [toDateString \(Método, Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString \(Método, Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)