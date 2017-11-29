---
title: "global (propiedad) (expresión Regular) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="global-property-regular-expression-javascript"></a>global (Propiedad, Regular Expression, JavaScript)
Devuelve un valor booleano que indica el estado del indicador global (**g**) utilizado con una expresión regular. Valor predeterminado es **false**. Sólo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `rgExp` referencia es una instancia de un **expresión Regular** objeto.  
  
 El `global` propiedad devuelve **true** si la marca global se establece para una expresión regular y devuelve **false** si no lo está.  
  
 Cuando se utiliza, la marca global indica que una búsqueda debe encontrar todas las apariciones del patrón dentro de la cadena buscada, no solo la primera de ellas. Se trata también conocido como coincidencia global.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `global` propiedad. Si se pasa **g** "en a la función que se muestra a continuación, todas las instancias de la palabra the" se reemplazan por la palabra "a". Tenga en cuenta que el "The" al principio de la cadena no se reemplaza porque la **i** (Omitir mayúsculas y minúsculas) marca no se pasa a la función.  
  
 Esta función muestra la condición de las propiedades asociadas a las marcas de expresión regular permitidas, que son **g**, **i**, y **m**. La función también muestra la cadena con todos los reemplazos realizados.  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Ejemplo  
 Aquí te mostramos la salida resultante.  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [ignoreCase (propiedad, Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [MultiLine (propiedad) (expresión Regular)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)