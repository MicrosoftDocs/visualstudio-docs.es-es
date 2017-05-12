---
title: "compare (Propiedad, Intl.Collator) | Microsoft Docs"
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# compare (Propiedad, Intl.Collator)
Devuelve una función que compara dos cadenas mediante el criterio de ordenación del intercalador.  
  
## Sintaxis  
  
```javascript  
collatorObj.compare  
```  
  
#### Parámetros  
 `collatorObj`  
 Requerido.  El nombre del objeto `Collator` para usar para la comparación.  
  
## Comentarios  
 La función devuelta por la propiedad `compare` toma dos argumentos, `x` y `y`, y devuelve el resultado de una comparación específica de la configuración regional `x` y `y` con las opciones especificadas en el objeto `Collator`.  
  
 El resultado de la comparación será:  
  
-   \-1 si `x` se produce antes de `y` en el criterio de ordenación.  
  
-   0 \(cero\) si `x` es igual a `y` en el criterio de ordenación.  
  
-   1 si `x` se produce después de `y` en el criterio de ordenación.  
  
## Ejemplo  
 El ejemplo siguiente crea un objeto `Collator` y realiza una comparación.  
  
```javascript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 El ejemplo siguiente usa un objeto `Collator` para buscar una cadena.  
  
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
 [Intl.Collator \(Objeto\)](../../javascript/reference/intl-collator-object-javascript.md)