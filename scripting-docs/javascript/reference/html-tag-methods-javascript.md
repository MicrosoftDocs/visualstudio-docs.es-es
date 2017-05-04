---
title: "M&#233;todos de etiqueta HTML (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "anchor (método) [JavaScript]"
  - "big (método) [JavaScript]"
  - "blink (método) [JavaScript]"
  - "bold (método) [JavaScript]"
  - "fixed (método) [JavaScript]"
  - "fontcolor (método) [JavaScript]"
  - "fontsize (método) [JavaScript]"
  - "métodos de etiqueta HTML [JavaScript]"
  - "italics (método) [JavaScript]"
  - "link (método) [JavaScript]"
  - "small (método) [JavaScript]"
  - "sub (método) [JavaScript]"
  - "sup (método) [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# M&#233;todos de etiqueta HTML (JavaScript)
Puedes usar métodos de etiquetas HTML para colocar elementos HTML alrededor del texto en un objeto `String`.  
  
## Sintaxis  
 En la tabla siguiente se muestra la sintaxis para cada método de etiquetas HTML y una descripción del mismo.  
  
 En la columna Sintaxis, `string1` es un objeto `String` o un literal de cadena.  
  
 La columna Estándar indica recomendaciones de [World Wide Web Consortium \(W3C\)](http://go.microsoft.com/fwlink/?LinkId=199553) para HTML 4.  "No recomendado" indica que se recomienda usar hojas de estilos en lugar del elemento HTML.  
  
|Sintaxis|Descripción del método|Descripción del parámetro|Estándar|  
|--------------|----------------------------|-------------------------------|--------------|  
|`string1`.anchor\(`name`\)|Pone un delimitador HTML que tiene un atributo NAME alrededor del texto.|El parámetro `name` es el texto que se va a colocar en el atributo NAME del delimitador HTML.||  
|`string1`.big\(\)|Pone etiquetas HTML \<BIG\> alrededor del texto.||No recomendado|  
|`string1`.blink\(\)|Pone etiquetas HTML \<BLINK\> alrededor del texto.  La etiqueta \<BLINK\>no se admite en Internet Explorer.||No estándar|  
|`string1`.bold\(\)|Pone etiquetas HTML \<B\> alrededor del texto.||No recomendado|  
|`string1`.fixed\(\)|Pone etiquetas HTML \<TT\> alrededor del texto.||No recomendado|  
|`string1`.fontcolor\(`color`\)|Pone etiquetas HTML \<FONT\> con un atributo COLOR alrededor del texto.|El parámetro `color` es un valor alfanumérico que contiene el valor hexadecimal o el nombre predefinido de un color.  Los nombres de colores predefinidos válidos dependen del explorador del host de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y su versión.|Desusado|  
|`string1`.fontsize\(`size`\)|Pone etiquetas HTML \<FONT\> con un atributo SIZE alrededor del texto.|El parámetro `size` es un valor entero que especifica el tamaño del texto.  Los valores enteros válidos dependen del explorador del host de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y su versión.|Desusado|  
|`string1`.italics\(\)|Pone etiquetas HTML \<I\> alrededor del texto.||No recomendado|  
|`string1`.link\(`href`\)|Pone un delimitador HTML que tiene un atributo HREF alrededor del texto.|El parámetro `href` es el texto que se va a colocar en el atributo HREF del delimitador HTML.||  
|`string1`.small\(\)|Pone etiquetas HTML \<SMALL\> alrededor del texto.||No recomendado|  
|`string1`.strike\(\)|Pone etiquetas HTML \<STRIKE\> alrededor del texto.||Desusado|  
|`string1`.sub\(\)|Pone etiquetas HTML \<SUB\> alrededor del texto.|||  
|`string1`.sup\(\)|Pone etiquetas HTML \<SUP\> alrededor del texto.|||  
  
## Comentarios  
 No se realiza ninguna comprobación para determinar si las etiquetas HTML ya se han aplicado a la cadena.  
  
## Ejemplo  
 En los ejemplos siguientes se muestra cómo usar los métodos de etiquetas HTML.  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)