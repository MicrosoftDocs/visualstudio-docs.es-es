---
title: toString (método) (objeto) (JavaScript) | Documentos de Microsoft
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
- toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641665"
---
# <a name="tostring-method-object-javascript"></a>toString (Método, Object de JavaScript)
Devuelve una representación de cadena de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Parámetros  
 `objectname`  
 Obligatorio. Objeto que se busca una representación de cadena.  
  
 `radix`  
 Opcional. Especifica una base para convertir valores numéricos en cadenas. Este valor solo se utiliza para los números.  
  
## <a name="remarks"></a>Comentarios  
 El **toString** método es un miembro de todos los integrados [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos. Cómo se comporta depende del tipo de objeto:  
  
|Objeto|Comportamiento|  
|------------|--------------|  
|Matriz|Elementos de un `Array` se convierten en cadenas. Las cadenas resultantes se concatenan, separados por comas.|  
|Booleano|Si el valor booleano es **true**, devuelve "`true`". De lo contrario, devuelve "`false`".|  
|Fecha|Devuelve la representación textual de la fecha.|  
|Error|Devuelve una cadena que contiene el mensaje de error asociado.|  
|Función|Devuelve una cadena con el formato siguiente, donde *functionname* es el nombre de la función cuyos **toString** se llamó el método:<br /><br /> `function functionname( ) { [native code] }`|  
|Número|Devuelve la representación textual del número.|  
|String|Devuelve el valor de la `String` objeto.|  
|Predeterminado|Devuelve `"[object objectname]"`, donde `objectname` es el nombre del tipo de objeto.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **toString** método con un argumento radix. El valor devuelto de función que se muestra a continuación es una tabla de conversión de base.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Se aplica a**: [objeto Array](../../javascript/reference/array-object-javascript.md)&#124; [Boolean (objeto)](../../javascript/reference/boolean-object-javascript.md)&#124; [Fecha objeto](../../javascript/reference/date-object-javascript.md)&#124; [Objeto error](../../javascript/reference/error-object-javascript.md)&#124; [Función objeto](../../javascript/reference/function-object-javascript.md)&#124; [Número objeto](../../javascript/reference/number-object-javascript.md)&#124; [Objeto Object](../../javascript/reference/object-object-javascript.md)&#124; [Objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [function (Instrucción)](../../javascript/reference/function-statement-javascript.md)