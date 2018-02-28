---
title: lastIndex (propiedad) (RegExp) (JavaScript) | Documentos de Microsoft
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
- lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex (Propiedad, RegExp de JavaScript)
Devuelve la posición del carácter donde comienza la siguiente coincidencia en una cadena de búsqueda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto asociado a esta propiedad siempre es global `RegExp` objeto.  
  
 El `lastIndex` propiedad está basado en cero, es decir, el índice del primer carácter es cero. Su valor inicial es -1. Siempre que se realiza una coincidencia correcta, se modifica su valor.  
  
 El `lastIndex` propiedad es modificada por el `exec` y **probar** métodos de la `RegExp` objeto y el `match`, **reemplazar**, y **dividir**métodos de la `String` objeto.  
  
 Las siguientes reglas se aplican a valores de `lastIndex`:  
  
-   Si no hay ninguna coincidencia, `lastIndex` se establece en -1.  
  
-   Si `lastIndex` es mayor que la longitud de la cadena, **probar** y `exec` producirá un error y `lastIndex` se establece en -1.  
  
-   Si `lastIndex` es igual a la longitud de la cadena, las coincidencias de expresiones regulares si el patrón coincide con la cadena vacía. En caso contrario, se produce un error en la búsqueda de coincidencias y `lastIndex` se restablece en -1.  
  
-   En caso contrario, `lastIndex` se establece en la siguiente posición de la coincidencia más reciente.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `lastIndex` propiedad. Esta función recorre en iteración una cadena de búsqueda e imprime el **índice** y `lastIndex` valores para cada palabra en la cadena.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)