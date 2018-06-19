---
title: Llame al método (función) (JavaScript) | Documentos de Microsoft
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
- call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634115"
---
# <a name="call-method-function-javascript"></a>call (Método, Function de JavaScript)
Llama a un método de un objeto y sustituye otro objeto para el objeto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `thisObj`  
 Opcional. El objeto que se usará como el objeto actual.  
  
 `arg1, arg2, , argN`  
 Opcional. Una lista de argumentos que se pasarán al método.  
  
## <a name="remarks"></a>Comentarios  
 El `call` método se usa para llamar a un método en nombre de otro objeto. Permite cambiar la `this` objeto de una función del contexto original al nuevo objeto especificado por `thisObj`.  
  
 Si `thisObj` no se proporciona, el `global` objeto se usa como `thisObj`.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo puede utilizar el método `call`.  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [apply (Método, Function)](../../javascript/reference/apply-method-function-javascript.md)