---
title: "arguments (propiedad) (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>arguments (Propiedad, Function de JavaScript)
Obtiene los argumentos para que se está ejecutando actualmente `Function` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Comentarios  
 El `function` argumento es el nombre de la función en ejecución y puede omitirse.  
  
 Esta propiedad permite a una función controlar un número variable de argumentos. El **longitud** propiedad de la `arguments` objeto contiene el número de argumentos pasados a la función. Los argumentos individuales contenidos en el `arguments` pueden tener acceso a objetos de la misma manera que se tiene acceso a elementos de la matriz.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `arguments`.  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [arguments (objeto)](../../javascript/reference/arguments-object-javascript.md)   
 [function (Instrucción)](../../javascript/reference/function-statement-javascript.md)