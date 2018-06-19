---
title: Buscar (método, String) (JavaScript) | Documentos de Microsoft
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
- search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639735"
---
# <a name="search-method-string-javascript"></a>search (Método, String, JavaScript)
Busca la primera coincidencia de subcadena en una búsqueda de expresión regular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. La `String` objeto o literal en el que se va a realizar la búsqueda de cadena.  
  
 `rgExp`  
 Obligatorio. Una instancia de un **expresión Regular** objeto que contiene el patrón de expresión regular y las marcas aplicables.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se encuentra una coincidencia, el **búsqueda** método devuelve un valor entero que indica el desplazamiento desde el principio de la cadena donde se produjo la primera coincidencia. Si se encuentra ninguna coincidencia, devuelve -1.  
  
## <a name="remarks"></a>Comentarios  
 También puede establecer el `i` marca que hace que la búsqueda distinguir mayúsculas de minúsculas.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **búsqueda** método.  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [exec (método, Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Match (método) (cadena)](../../javascript/reference/match-method-string-javascript.md)   
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Replace (método) (cadena)](../../javascript/reference/replace-method-string-javascript.md)   
 [Test (método) (expresión Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programación de la expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)