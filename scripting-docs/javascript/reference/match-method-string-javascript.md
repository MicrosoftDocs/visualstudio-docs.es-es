---
title: "Match (método) (cadena) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>match (Método, String de JavaScript)
Coincide con una cadena con una expresión regular y devuelve una matriz que contiene los resultados de búsqueda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. La `String` objeto o literal en el que se va a realizar la búsqueda de cadena.  
  
 `rgExp`  
 Obligatorio. Un objeto de expresión regular que contiene el patrón de expresión regular y las marcas aplicables. Esto también puede ser un nombre de variable o una cadena literal que contiene el patrón de expresión regular y las marcas.  
  
## <a name="remarks"></a>Comentarios  
 Si el `match` método no encuentra una coincidencia, devuelve `null`. Si encuentra una coincidencia, `match` devuelve una matriz y las propiedades de la información global `RegExp` objeto se actualizan para reflejar los resultados de la búsqueda de coincidencias.  
  
 Si la marca global (`g`) no se establece, elemento cero de la matriz contiene toda la coincidencia, mientras que los elementos 1 a través de  *n*  contienen subcoincidencias. Este comportamiento es el mismo que el comportamiento de la [exec (método) (expresión Regular)](../../javascript/reference/exec-method-regular-expression-javascript.md) cuando no se establece la marca global. Si se establece la marca global, elementos del 0 al  *n*  contienen todas las coincidencias que se ha producido.  
  
 Si la marca global no se establece, la matriz devuelta por la `match` método tiene dos propiedades, `input` y `index`. El `input` propiedad contiene toda la cadena buscada. El `index` propiedad contiene la posición de la subcadena coincidente dentro de la cadena de búsqueda completa.  
  
 Si la marca `i` está establecido, la búsqueda no distingue entre mayúsculas y minúsculas.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `match`.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [exec (método, Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Replace (método) (cadena)](../../javascript/reference/replace-method-string-javascript.md)   
 [Buscar (método, String)](../../javascript/reference/search-method-string-javascript.md)   
 [Test (método) (expresión Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programación de la expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternancia y subexpresiones (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Referencias inversas (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)