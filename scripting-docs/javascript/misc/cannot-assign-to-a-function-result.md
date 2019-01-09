---
title: No se puede asignar al resultado de una función | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a29c3f20392dc216c0306137c0dec6b22aaa58a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093866"
---
# <a name="cannot-assign-to-a-function-result"></a>No se puede asignar al resultado de una función
Se intentó asignar un valor a un resultado de la función. El resultado de una función puede asignarse a una variable, pero no se puede usar como una variable. Si desea asignar un nuevo valor a la propia función, omitir los paréntesis (operador de llamada de función). El ejemplo siguiente muestra una situación en la que se genera este error.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   No use el valor de resultado de una llamada de función como algo que puede *asignar a*. Puede asignar el resultado de la llamada de función *a una variable* aunque.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Como alternativa, puede asignar la función propia (y no el valor devuelto) a una variable.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [Escribir código JavaScript](../../javascript/writing-javascript-code.md)   
 [Funciones](../../javascript/functions-javascript.md)