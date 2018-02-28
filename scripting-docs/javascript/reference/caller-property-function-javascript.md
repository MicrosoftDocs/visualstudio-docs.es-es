---
title: "caller (propiedad) (función) (JavaScript) | Documentos de Microsoft"
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
- caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>caller (Propiedad, Function de JavaScript)
Obtiene la función que invoca la función actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>Comentarios  
 La `functionName` objeto se está ejecutando el nombre de cualquier función.  
  
 El `caller` propiedad está definida para una función solo mientras que se ejecute la función. Si la función se llama desde la parte superior de un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] programa, `caller` contiene `null`.  
  
 Si el `caller` propiedad se utiliza en un contexto de cadena, el resultado es el mismo que `functionName`.`toString`, es decir, se muestra el texto de la función descompilado.  
  
 En el ejemplo siguiente se muestra el uso de la propiedad `caller`.  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [function (Instrucción)](../../javascript/reference/function-statement-javascript.md)