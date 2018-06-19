---
title: Métodos de etiqueta HTML (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638655"
---
# <a name="html-tag-methods-javascript"></a>Métodos de etiqueta HTML (JavaScript)
Puede usar los métodos de etiqueta HTML para colocar elementos HTML alrededor del texto de un `String` objeto.  
  
## <a name="syntax"></a>Sintaxis  
 En la tabla siguiente se muestra la sintaxis y una descripción de cada método de etiqueta HTML.  
  
 En la columna de la sintaxis, `string1` es un `String` literal u objeto.  
  
 Indica la columna estándar [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) recomendaciones para HTML 4. "Desaconseja" indica que el elemento HTML se desaconseja en favor de hojas de estilos.  
  
|Sintaxis|Descripción del método|Descripción del parámetro|Estándar|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Coloca un delimitador HTML que tiene un atributo de nombre alrededor del texto.|El `name` parámetro es texto que se va a colocar en el atributo NAME del delimitador HTML.||  
|`string1`.big()|Coloca HTML \<BIG > etiquetas alrededor del texto.||No usar|  
|`string1`.blink()|Coloca HTML \<BLINK > etiquetas alrededor del texto. El \<BLINK > etiqueta no se admite en Internet Explorer.||No en estándar|  
|`string1`.Bold()|Coloca HTML \<B > etiquetas alrededor del texto.||No usar|  
|`string1`.fixed()|Coloca HTML \<TT > etiquetas alrededor del texto.||No usar|  
|`string1`.fontcolor (`color`)|Coloca HTML \<fuente > etiquetas con un atributo COLOR a ambos lados del texto.|El `color` parámetro es un valor de cadena que contiene el valor hexadecimal o el nombre predefinido para un color. Nombres de colores predefinidos válidos dependen del [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] explorador y su versión de host.|En desuso|  
|`string1`.FontSize (`size`)|Coloca HTML \<fuente > etiquetas con un atributo SIZE alrededor del texto.|El `size` parámetro es un valor entero que especifica el tamaño del texto. Valores enteros válidos dependen del [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] explorador y su versión de host.|En desuso|  
|`string1`.italics()|Coloca HTML \<I > etiquetas alrededor del texto.||No usar|  
|`string1`.Link (`href`)|Coloca un delimitador HTML que tiene un atributo HREF alrededor del texto.|El `href` parámetro es texto que se va a colocar en el atributo HREF del delimitador HTML.||  
|`string1`.Small()|Coloca HTML \<pequeño > etiquetas alrededor del texto.||No usar|  
|`string1`.Strike()|Coloca HTML \<STRIKE > etiquetas alrededor del texto.||En desuso|  
|`string1`.Sub()|Coloca HTML \<SUB > etiquetas alrededor del texto.|||  
|`string1`.SUP()|Coloca HTML \<SUP > etiquetas alrededor del texto.|||  
  
## <a name="remarks"></a>Comentarios  
 Se realiza ninguna comprobación para determinar si las etiquetas HTML ya se han aplicado a la cadena.  
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran cómo usar los métodos de etiqueta HTML.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)