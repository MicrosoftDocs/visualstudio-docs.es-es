---
title: Usar expresiones regulares en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
- Visual Studio, regular expressions
ms.assetid: 718a617d-0e05-47e1-a218-9746971527f4
caps.latest.revision: 53
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 541b728d006f85fc550c5ddad2a7cd74190c244a
ms.contentlocale: es-es
ms.lasthandoff: 05/30/2017

---
# <a name="using-regular-expressions-in-visual-studio"></a>Usar expresiones regulares en Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa expresiones regulares de .NET Framework para buscar y reemplazar texto. Para obtener más información sobre las expresiones regulares de .NET, consulte [Expresiones regulares de .NET Framework](/dotnet/standard/base-types/regular-expressions).  
  
 En las versiones previas a Visual Studio 2012, se usaba una sintaxis de expresiones regulares personalizadas en las ventanas Buscar y Reemplazar. Consulte [Usar expresiones regulares en Visual Studio](https://msdn.microsoft.com/en-us/library/2k3te2cs\(v=vs.110\).aspx) para ver una explicación de cómo convertir a las versiones de .NET algunos de los símbolos de expresiones regulares personalizadas más frecuentes.  
  
> [!TIP]
>  En sistemas operativos Windows, la mayoría de las líneas terminan en "\r\n" (un retorno de carro seguido de una nueva línea). Estos caracteres no se ven, pero están presentes en el editor y se pasan al servicio de expresiones regulares de .NET.  
  
> [!TIP]
>  Para obtener información sobre las expresiones regulares que se usan en patrones de reemplazo, consulte [Sustituciones](/dotnet/standard/base-types/substitutions-in-regular-expressions). Para usar un grupo de captura numerado, la sintaxis es `$1` para especificar el grupo numerado y `(x)` para especificar el grupo en cuestión. Por ejemplo, la expresión regular agrupada `(\d)([a-z])` encuentra cuatro coincidencias en la siguiente cadena: **1a 2b 3c 4d**. La cadena de reemplazo `z$1` convierte esa cadena a **z1 z2 z3 z4**.  
  
## <a name="regular-expressions-in-visual-studio"></a>Expresiones regulares en Visual Studio  
 Estos son algunos ejemplos:  
  
|Propósito|Expresión|Ejemplo|  
|-------------|----------------|-------------|  
|Coincidencia con cualquier carácter (excepto un salto de línea)|.|`a.o` coincide con "aro" en "around" y "abo" en "about", pero no con "acro" en "across".|  
|Coincidencia con cero o más apariciones de la expresión anterior (coincidencias con tantos caracteres como sea posible)|*|`a*r` coincide con "r" en "rack", "ar" en "ark" y "aar" en "aardvark".|  
|Coincidencia con cualquier carácter cero o más veces (carácter comodín *)|.*|c.*e coincide con "cke" en "racket", "comme" en "comment", y "code" en "code"|  
|Coincidencia con una o más apariciones de la expresión anterior (coincidencia con tantos caracteres como sea posible)|+|`e.+e` coincide con "eede" en "feeder", pero no con "ee".|  
|Coincidencia con cualquier carácter una o más veces (carácter comodín ?)|.+|e.+e coincide con “eede” en “feeder”, pero no con “ee”.|  
|Coincidencia con cero o más apariciones de la expresión anterior (coincidencia con el menor número de caracteres posible)|*?|`e.*?e` coincide con "ee" en "feeder", pero no con "eede".|  
|Coincidencia con una o más apariciones de la expresión anterior (coincidencia con el menor número de caracteres posible)|+?|`e.+?e` coincide con "ente" y "erprise" en "enterprise", pero no con toda la palabra "enterprise".|  
|Delimitar la cadena coincidente al principio de una cadena o línea|^|`^car` coincide con la palabra "car" solo cuando aparece al principio de una línea.|  
|Delimitar la cadena coincidente al final de una línea|\r?$|`End\r?$` coincide con "end" solo cuando aparece al final de una línea.|  
|Coincidencia con cualquier carácter único de un conjunto|[abc]|`b[abc]` coincide con "ba", "bb" y "bc".|  
|Coincidir con cualquier carácter de un intervalo de caracteres|[a-f]|`be[n-t]` coincide con "bet" en "between", "ben" en "beneath" y "bes" en "beside", pero no "below".|  
|Capturar y numerar implícitamente la expresión contenida entre paréntesis|()|`([a-z])X\1` coincide con "aXa" y "bXb", pero no con "aXb". ". "\1" hace referencia al primer grupo de expresión "[a-z]".|  
|Invalidar una coincidencia|(?!abc)|`real (?!ity)` coincide con "real" en "realty" y "really", pero no con "reality". También encuentra el segundo “real” (pero no el primero) en “realityreal”.|  
|Coincidir con cualquier carácter que no está en un conjunto determinado de caracteres|[^abc]|`be[^n-t]` coincide con "bef" en "before", "beh" en "behind" y "bel" en "below", pero no con "beneath".|  
|Coincidir con la expresión situada antes o después del símbolo|&#124;|`(sponge&#124;mud) bath` coincide con "sponge bath" y "mud bath".|  
|Escape del carácter que sigue a la barra diagonal inversa|\|`\^` coincide con el carácter ^.|  
|Especificar el número de apariciones del carácter o grupo precedente|{x}, donde x es el número de apariciones|`x(ab){2}x` coincide con "xababx" y `x(ab){2,3}x` coincide con "xababx" y "xabababx", pero no con "xababababx".|  
|Coincidir con el texto de una clase de caracteres Unicode, donde "X" es el número de Unicode. Para obtener más información sobre clases de caracteres Unicode, consulte el documento sobre<br /><br /> [Unicode Standard 5.2 Character Properties](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf) (Propiedades de caracteres del estándar Unicode 5.2).|\p{X}|`\p{Lu}` coincide con "T" y "D" en "Thomas Doe".|  
|Coincidir con un límite de palabras|`\b` (fuera de una clase de caracteres \b especifica un límite de palabras y dentro de una clase de caracteres especifica un retroceso).|`\bin` coincide con "in" en "inside", pero no con "pinto".|  
|Coincidir con un salto de línea (es decir, con un retorno de carro seguido de una nueva línea)|\r?\n|`End\r?\nBegin` coincide con "End" y "Begin" solo cuando "End" es la última cadena en una línea y "Begin" es la primera cadena en la línea siguiente.|  
|Coincidir con cualquier carácter alfanumérico|\w|`a\wd` coincide con "add" y "a1d", pero no con "a d".|  
|Coincidir con cualquier carácter de espacio en blanco|(?([^\r\n])\s)|`Public\sInterface` coincide con la frase "Public Interface".|  
|Coincidir con cualquier carácter numérico|\d|`\d` coincide con "3" en "3456", "2" en "23" y "1" en "1".|  
|Coincidir con un carácter Unicode|\uXXXX donde XXXX especifica el valor del carácter Unicode.|`\u0065` coincide con el carácter "e".|  
|Coincidir con un identificador|\b(_\w+&#124;[\w-[0-9\_]]\w*)\b|Coincide con “type1”, pero no con “&type1” o “#define”.|  
|Coincidir con una cadena entre comillas|((\\".+?\\")&#124;('.+?'))|Coincide con cualquier cadena entre comillas simples o dobles.|  
|Coincidir con un número hexadecimal|\b0[xX]([0-9a-fA-F]\)\b|Coincide con “0xc67f”, pero no con “0xc67fc67f”.|  
|Coincidir con enteros y decimales|\b[0-9]*\\.\*[0-9]+\b|Coincide con “1.333”.|  
  
## <a name="see-also"></a>Vea también  
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)
