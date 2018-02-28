---
title: "MultiLine (propiedad) (expresión Regular) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline (Propiedad, Regular Expression de JavaScript)
Devuelve un valor booleano que indica el estado del indicador multilínea (**m**) utilizado con una expresión regular. Valor predeterminado es **false**. Sólo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `rgExp` argumento es una instancia de la `RegExp` objeto  
  
 El **varias líneas** propiedad devuelve **true** si el indicador multiline se establece para una expresión regular y devuelve **false** si no lo está. El **varias líneas** propiedad es **true** si se creó el objeto de expresión regular con la **m** marca.  
  
 Si **varias líneas** es **false**, "^" coincide con la posición al principio de una cadena y "$" coincide con la posición al final de una cadena. Si **varias líneas** es **true**, "^" coincide con la posición al principio de una cadena, así como la posición siguiente de un "\n" o "\r" y "$" coincide con la posición al final de una cadena y la posición anterior a "\n "o"\r".  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el comportamiento de la **multilínea** propiedad. Si se pasa "m" a la función que se muestra a continuación, la palabra "while" se reemplaza por la palabra "and". Esto es porque está configurada con la marca de varias líneas y la palabra "while" se produce al principio de la línea después de un carácter de nueva línea. El indicador multiline permite que la búsqueda se realizará en cadenas de varias líneas.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [global (propiedad, Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase (propiedad, Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)