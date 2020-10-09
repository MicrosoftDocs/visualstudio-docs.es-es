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
ms.openlocfilehash: 6aab43ec6a547982cf670d64c8ad8b752160839f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862339"
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
 [Objeto de función](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Escribir código JavaScript](https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web/JavaScript_basics)   
 [Funciones](https://developer.mozilla.org/docs/Learn/JavaScript/Building_blocks/Functions)