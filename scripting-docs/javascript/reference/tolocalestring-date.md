---
title: "toLocaleString (Date) | Microsoft Docs"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
Convierte una fecha en una cadena mediante la configuración regional actual o especificada.  
  
## Sintaxis  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### Parámetros  
 `dateObj`  
 Requerido.  Objeto `Date` que se va a convertir.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de la configuración regional, enumérelas en orden descendente de prioridad para de manera que la primera entrada se la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional.  Un objeto que contiene una o más propiedades que especifican opciones de comparación.  
  
## Comentarios  
 A partir de Internet Explorer 11, `toLocaleString` utiliza `Intl.DateTimeFormat` internamente para crear comparaciones, lo que agrega compatibilidad para los parámetros `locales` y `options`.  Para obtener más información sobre estos parámetros, vea [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento y versiones de explorador.  Para obtener más información, consulte la sección Requisitos.  
  
 Cuando usa `toLocaleString` en modo "quirks", en modo de documento anterior y en modo de documento estándar de Internet Explorer 10:  
  
-   Devuelve un objeto `String` que contiene la fecha escrita en el formato largo predeterminado de la configuración regional actual.  
  
-   Para fechas comprendidas entre 1601 y 1999 d.C., se aplica formato a la fecha de acuerdo con la configuración regional del Panel de control del usuario.  
  
> [!NOTE]
>  Si omite el parámetro `locales`, utilice `toLocaleString` para mostrar solo los resultados a un usuario; nunca utilícelo para calcular valores desde un script, porque el resultado devuelto es específico del equipo.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleString` con opciones de configuración regional y comparación especificadas.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Los parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [toLocaleDateString \(Método, Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)