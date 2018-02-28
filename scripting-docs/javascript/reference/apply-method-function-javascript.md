---
title: "Apply (método) (función) (JavaScript) | Documentos de Microsoft"
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
- apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="apply-method-function-javascript"></a>apply (Método, Function de JavaScript)
Llama a la función, sustituyendo el objeto especificado para la `this` valor de la función y la matriz especificada por los argumentos de la función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `thisObj`  
 Opcional. El objeto que se usará como el `this` objeto.  
  
 `argArray`  
 Opcional. Un conjunto de argumentos que se pasan a la función.  
  
## <a name="remarks"></a>Comentarios  
 Si `argArray` no es un objeto válido, a continuación, se produce un error de "Espera de objeto".  
  
 Si no `argArray` ni `thisObj` se proporcionan, la versión original `this` objeto se usa como `thisObj` y se pasa ningún argumento.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar el método apply.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Function (Objeto)](../../javascript/reference/function-object-javascript.md)