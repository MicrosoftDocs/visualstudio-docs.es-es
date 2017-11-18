---
title: "exec (método) (expresión Regular) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>exec (Método, Regular Expression de JavaScript)
Ejecuta una búsqueda en una cadena con un patrón de expresión regular y devuelve una matriz que contiene los resultados de búsqueda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Parámetros  
 `rgExp`  
 Obligatorio. Una instancia de un **expresión Regular** objeto que contiene el patrón de expresión regular y las marcas aplicables.  
  
 `str`  
 Obligatorio. La `String` objeto o literal en el que se va a realizar la búsqueda de cadena.  
  
## <a name="remarks"></a>Comentarios  
 Si el `exec` método no encuentra una coincidencia, devuelve `null`. Si encuentra una coincidencia, `exec` devuelve una matriz y las propiedades de la información global `RegExp` objeto se actualizan para reflejar los resultados de la búsqueda de coincidencias. El elemento cero de la matriz contiene toda la coincidencia, mientras que los elementos 1 -  *n*  contienen subcoincidencias que se han producido dentro de la coincidencia. Este comportamiento es idéntico al comportamiento de la `match` método sin la marca global (**g**) establecido.  
  
 Si se establece la marca global para una expresión regular, `exec` busca la cadena que empieza en la posición indicada por el valor de `lastIndex`. Si no se establece la marca global, `exec` omite el valor de `lastIndex` y busca desde el principio de la cadena.  
  
 La matriz devuelta por la `exec` método tiene tres propiedades **entrada**, **índice** y **lastIndex.** El **entrada** propiedad contiene toda la cadena buscada. El **índice** propiedad contiene la posición de la subcadena coincidente dentro de la cadena de búsqueda completa. El `lastIndex` propiedad contiene la posición después del último carácter en la coincidencia.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `exec` método:  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Match (método) (cadena)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Buscar (método, String)](../../javascript/reference/search-method-string-javascript.md)   
 [Test (método) (expresión Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programación de la expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)