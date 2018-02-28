---
title: arguments (objeto) (JavaScript) | Documentos de Microsoft
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>arguments (Objeto de JavaScript)
Objeto que representa los argumentos en la función en ejecución y las funciones que lo han llamado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Parámetros  
 *function*  
 Opcional. El nombre de la ejecución `Function` objeto.  
  
 *n*  
 Obligatorio. Índice de base cero a valores de argumento pasado a la `Function` objeto.  
  
## <a name="remarks"></a>Comentarios  
 No se puede crear explícitamente un **argumentos** objeto. El **argumentos** objeto solo está disponible cuando una función inicia la ejecución. El **argumentos** objeto de la función no es una matriz, pero los argumentos individuales se tiene acceso a la misma manera que se tiene acceso a elementos de la matriz. El índice  *n*  es realmente una referencia a uno de los **0**  ***n***  propiedades de la **argumentos** objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **argumentos** objeto.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [0... n (propiedades) (argumentos)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee (propiedad) (argumentos)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length (Propiedad, Argumentos)](../../javascript/reference/length-property-arguments-javascript.md)