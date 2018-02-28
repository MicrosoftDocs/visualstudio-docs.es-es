---
title: "No se puede asignar al resultado de una función | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-a-function-result"></a>No se puede asignar al resultado de una función
Se intentó asignar un valor al resultado de una función. El resultado de una función puede asignarse a una variable, pero no se puede usar como una variable. Si desea asignar un nuevo valor a la propia función, omita los paréntesis (operador de llamada de función). En el ejemplo siguiente se muestra una situación en la que se genera este error.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   No use el valor de resultado de una llamada de función como algo que puede *asignar a*. Puede asignar el resultado de la llamada de función *a una variable* aunque.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Como alternativa, puede asignar la función propia (y no su valor devuelto) a una variable.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [Escribir código JavaScript](../../javascript/writing-javascript-code.md)   
 [Funciones](../../javascript/functions-javascript.md)