---
title: "localeCompare (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare (método)"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# localeCompare (M&#233;todo, String de JavaScript)
Determina si dos cadenas son equivalentes en la configuración regional actual.  
  
## Sintaxis  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## Parámetros  
 `stringVar`  
 Requerido.  La primera cadena que se va a comparar.  
  
 `stringExp`  
 Requerido.  La segunda cadena que se va a comparar.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de la configuración regional, enumérelas en orden descendente de prioridad para de manera que la primera entrada se la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  Este parámetro debe ajustarse a los estándares [BCP 47](http://tools.ietf.org/html/rfc5646); vea el [objeto International.Collator](../../javascript/reference/intl-collator-object-javascript.md) para obtener más información.  
  
 `options`  
 Opcional.  Objeto que contiene una o más propiedades que especifican opciones de comparación. Vea el [objeto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) para obtener más información.  
  
## Comentarios  
 Para las cadenas de comparación, puede especificar objetos `String` o los literales de cadena.  
  
 A partir de Internet Explorer 11, `localeCompare` utiliza el objeto `Intl.Collator` internamente para crear comparaciones, lo que agrega compatibilidad para los parámetros `locales` y `options`.  Para obtener más información sobre estos parámetros, vea [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) y [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento y versiones de explorador.  Para obtener más información, consulte la sección Requisitos.  
  
 El método `localeCompare` realiza una comparación de la cadena actual y la cadena `stringVar` y `stringExp` y devuelve uno de los siguientes resultados, en función del criterio de ordenación de la configuración regional predeterminada del sistema:  
  
-   \-1 si ordena `stringVar` antes de `stringExp`.  
  
-   \+1 si `stringVar` se ordena después de `stringExp`.  
  
-   0 \(cero\) si las dos cadenas son equivalentes.  
  
## Ejemplo  
 En el siguiente código se muestra cómo usar `localeCompare`.  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## Ejemplo  
 El código siguiente muestra cómo utilizar `localeCompare` con la configuración regional Alemán \(Alemania\).  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar `localeCompare` con la configuración regional de alemán \(Alemania\) y una extensión específica de la configuración regional que indique el criterio de ordenación de las libretas de teléfonos alemanas.  Este ejemplo muestra diferencias específicas de configuración regional.  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Los parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [toLocaleString \(Método, Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)