---
title: ignoreCase (propiedad) (expresión Regular) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637865"
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase (Propiedad, Regular Expression de JavaScript)
Devuelve un valor booleano que indica el estado del indicador ignoreCase (**i**) utilizado con una expresión regular. Valor predeterminado es **false**. Sólo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `rgExp` referencia es una instancia de la `RegExp` objeto.  
  
 El **ignoreCase** propiedad devuelve **true** si el indicador ignoreCase se establece para una expresión regular y devuelve **false** si no lo está.  
  
 El indicador ignoreCase, cuando se utiliza, indica que una búsqueda debe omitir mayúsculas y minúsculas al buscar el modelo en la cadena buscada.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **ignoreCase** propiedad. Si se pasa "gi" a la función que se muestra a continuación, todas las instancias de la palabra "the" se reemplazan con la palabra "a", incluida la inicial "The". Esto es porque con el indicador ignoreCase establecido, la búsqueda no distingue entre mayúsculas y minúsculas. Por lo que "T" es igual a "t" para los propósitos de búsqueda de coincidencias.  
  
 Esta función devuelve los valores booleanos que indican el estado de las marcas de expresión regular permitidas, que son **g**, **i**, y **m**. La función también devuelve la cadena con todos los reemplazos realizados.  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Ejemplo  
 Aquí te mostramos la salida resultante.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [global (propiedad, Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [MultiLine (propiedad) (expresión Regular)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)