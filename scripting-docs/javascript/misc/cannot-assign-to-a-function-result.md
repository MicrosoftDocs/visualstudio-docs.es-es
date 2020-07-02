---
title: No se puede asignar a un resultado de función | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817637"
---
# <a name="cannot-assign-to-a-function-result"></a>No se puede asignar al resultado de una función
Ha intentado asignar un valor a un resultado de la función. El resultado de una función se puede asignar a una variable, pero no se puede usar como una variable. Si desea asignar un nuevo valor a la propia función, omita los paréntesis (el operador de llamada de función). En el ejemplo siguiente se muestra una situación en la que se genera este error.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- No use el valor de un resultado de llamada de función como algo que puede *asignar a*. Sin embargo, puede asignar el resultado de la llamada de función *a una variable* .  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Como alternativa, puede asignar la propia función (y no su valor devuelto) a una variable.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [Escribir código JavaScript](../../javascript/writing-javascript-code.md)   
 [Funciones](../../javascript/functions-javascript.md)