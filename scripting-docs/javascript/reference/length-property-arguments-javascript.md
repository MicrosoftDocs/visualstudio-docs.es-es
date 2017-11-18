---
title: Length (propiedad, argumentos) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>length (Propiedad, argumentos de JavaScript)
Devuelve el número real de argumentos pasados a una función por el llamador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional *función* argumento es el nombre de la ejecución `Function` objeto.  
  
 El **longitud** propiedad de la **argumentos** objeto se inicializa el motor de scripting en el número real de argumentos pasados a una `Function` objeto cuando comienza la ejecución de esa función.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **longitud** propiedad de la **argumentos** objeto. Para comprender el ejemplo, pasar más argumentos a la función de los 2 argumentos que se esperaba:  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [arguments (objeto)](../../javascript/reference/arguments-object-javascript.md)&#124; [Objeto de función](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [arguments (propiedad) (función)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Length (propiedad, Array)](../../javascript/reference/length-property-array-javascript.md)   
 [length (Propiedad, String)](../../javascript/reference/length-property-string-javascript.md)