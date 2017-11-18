---
title: "Test (método) (expresión Regular) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="test-method-regular-expression-javascript"></a>test (Método, Regular Expression de JavaScript)
Devuelve un valor booleano que indica si existe o no un modelo en una cadena de búsqueda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>Parámetros  
 `rgExp`  
 Obligatorio. Una instancia de un **expresión Regular** objeto que contiene el patrón de expresión regular y las marcas aplicables.  
  
 `str`  
 Obligatorio. La cadena en la que se va a realizar la búsqueda.  
  
## <a name="remarks"></a>Comentarios  
 El **probar** método comprueba si un patrón existe dentro de una cadena y devuelve **true** si es así, y **false** en caso contrario.  
  
 Las propiedades de la información global `RegExp` objeto no se modifica la **probar** método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **probar** método. Para usar este ejemplo, pasar la función de un patrón de expresión regular y una cadena. La función probará la aparición de un patrón de expresión regular en la cadena y devolver una cadena que indica los resultados de búsqueda:  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)