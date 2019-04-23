---
title: No se puede asignar al resultado de una función | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226056f139e45f432d757aff8f8774b013742de3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076817"
---
# <a name="cannot-assign-to-a-function-result"></a>No se puede asignar al resultado de una función
Se intentó asignar un valor a un resultado de la función. El resultado de una función puede asignarse a una variable, pero no se puede usar como una variable. Si desea asignar un nuevo valor a la propia función, omitir los paréntesis (operador de llamada de función). El ejemplo siguiente muestra una situación en la que se genera este error.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- No use el valor de resultado de una llamada de función como algo que puede *asignar a*. Puede asignar el resultado de la llamada de función *a una variable* aunque.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Como alternativa, puede asignar la función propia (y no el valor devuelto) a una variable.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [Escribir código JavaScript](../../javascript/writing-javascript-code.md)   
 [Funciones](../../javascript/functions-javascript.md)