---
title: callee (propiedad, argumentos) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="callee-property-arguments-javascript"></a>callee (Propiedad, arguments de JavaScript)
Devuelve el `Function` objeto que se está ejecutando, es decir, el texto del cuerpo del elemento especificado `Function` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional *función* argumento es el nombre de la ejecución `Function` objeto.  
  
 El `callee` propiedad es un miembro de la **argumentos** objeto que está disponible solo cuando se ejecuta la función asociada.  
  
 El valor inicial de la `callee` propiedad es el `Function` del objeto que se está ejecutando. Esto permite que las funciones anónimas sean recursivas.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [arguments (objeto)](../../javascript/reference/arguments-object-javascript.md)&#124; [Objeto de función](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [caller (Propiedad, Function)](../../javascript/reference/caller-property-function-javascript.md)