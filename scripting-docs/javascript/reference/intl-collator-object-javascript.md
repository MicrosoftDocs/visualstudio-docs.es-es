---
title: "Intl.Collator (Objeto, JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.Collator (Objeto, JavaScript)
Proporciona comparaciones de cadenas específicas de la configuración regional.  
  
## Sintaxis  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### Parámetros  
 `collatorObj`  
 Requerido.  El nombre de la variable al que se va a asignar el objeto de `Collator`.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de la configuración regional, enumérelas en orden descendente de prioridad para de manera que la primera entrada se la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  Vea la sección Comentarios para obtener más información.  
  
 `options`  
 Opcional.  Un objeto que contiene una o más propiedades que especifican opciones de comparación.  Vea la sección Comentarios para obtener más detalles.  
  
## Comentarios  
 El parámetro `locales` debe ajustarse al lenguaje [BCP 47](http://tools.ietf.org/html/rfc5646) o las etiquetas de configuración regional como “en\-US” y “zh\-Hans\-CN".  La etiqueta puede incluir el lenguaje, la región, el país y la variante.  Para obtener una lista de idiomas, vea [Registro de subetiquetas del lenguaje IANA](http://go.microsoft.com/fwlink/p/?linkid=227303).  Para obtener ejemplos de etiquetas de lenguaje, vea el [Apéndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47.  Para `Collator`, puede incluir la extensión de \-u en la cadena de la configuración regional especificar una o varias de las extensiones Unicode siguientes:  
  
-   \- co para especificar las intercalaciones variables \(configuración regional específicas\):"*language*\-*region*\-u\-co\-*value*".  
  
-   \-kn para especificar una comparación numérica: "*language*\-*region*\-u\-kn\-true&#124;false".  
  
-   –kf para especificar si primero se deben ordenar los caracteres en mayúscula o los caracteres en minúscula: "*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\).  Actualmente, esta extensión no es compatible.  
  
 Para especificar una comparación numérica, puede establecer la extensión – kn en la cadena de configuración regional o utilizar la propiedad `numeric` del parámetro `options` .  Si usa la propiedad `numeric`, el valor –kn no se aplicará.  
  
 El parámetro `options` puede incluir las siguientes propiedades:  
  
-   `localeMatcher`.  Especifica el algoritmo de coincidencia de configuración regional que se debe usar.  Los valores posibles son “lookup” y “best fit”.  El valor predeterminado es "best fit".  
  
-   `usage`.  Especifica si el objetivo de la comparación es ordenar o buscar.  Los valores posibles son "sort" y "search".  El valor predeterminado es "sort".  
  
-   `sensitivity`.  Especifica la distinción del intercalador.  Los valores posibles son "base", "accent", "case" y "variant".  El valor predeterminado es `undefined`.  
  
-   `ignorePunctuation`.  Especifica si la puntuación se omite en la comparación.  Los valores posibles son "true" y "false".  El valor predeterminado es `false`.  
  
-   `numeric`.  Especifica si se usar la ordenación numérica.  Los valores posibles son "true" y "false".  El valor predeterminado es `false`.  
  
-   `caseFirst`.  No se admite en la actualidad.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Collator`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Devuelve una función que compara dos cadenas mediante el criterio de ordenación del intercalador.|  
|[Constructor](../../javascript/reference/constructor-property-intl-collator.md)|Especifica la función que crea un intercalador.|  
|[prototipo](../../javascript/reference/prototype-property-intl-collator.md)|Devuelve una referencia al prototipo para un intercalador.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Collator`.  
  
|||  
|-|-|  
|Método|Descripción|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Devuelve un objeto que contiene las propiedades y los valores del intercalador.|  
  
## Ejemplo  
 El ejemplo siguiente crea un objeto `Collator` y realiza una comparación.  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## Ejemplo  
 El ejemplo siguiente usa objetos `Collator` para ordenar una matriz.  Este ejemplo muestra diferencias específicas de configuración regional.  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente usa un objeto `Collator` para buscar una cadena y especifica opciones de comparación.  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [localeCompare \(Método, String\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat \(Objeto\)](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat \(Objeto\)](../../javascript/reference/intl-numberformat-object-javascript.md)