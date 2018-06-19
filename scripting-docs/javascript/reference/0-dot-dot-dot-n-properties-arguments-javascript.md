---
title: 0... n (propiedades) (argumentos) (JavaScript) | Documentos de Microsoft
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
- 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634015"
---
# <a name="0n-properties-arguments-javascript"></a>0...n (Propiedades, arguments de JavaScript)
Devuelve el valor real de argumentos individuales de un **argumentos** objeto devuelto por la **argumentos** propiedad de una función que se ejecuta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Parámetros  
 *function*  
 Opcional. El nombre de la ejecución `Function` objeto.  
  
 0, 1, 2, *, n*  
 Obligatorio. Entero no negativo en el intervalo de 0 a  *n*  donde 0 representa el primer argumento y  *n*  representa el argumento final. El valor del argumento final  *n*  es **arguments.length-1**.  
  
## <a name="remarks"></a>Comentarios  
 Los valores devueltos por el 0. . . n (propiedades) son los valores reales que se pasa a la función que se ejecuta. Mientras no realmente una matriz de argumentos, los argumentos individuales que componen el **argumentos** objeto se obtiene acceso a la misma manera que se tiene acceso a elementos de la matriz.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **0...**  ***n***propiedades de la **argumentos** objeto. Para comprender el ejemplo, pase uno o más argumentos a la función:  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [arguments (objeto)](../../javascript/reference/arguments-object-javascript.md)&#124; [Objeto de función](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Length (propiedad, argumentos)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length (Propiedad, Function)](../../javascript/reference/length-property-function-javascript.md)