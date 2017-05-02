---
title: "No se puede asignar al resultado de una funci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# No se puede asignar al resultado de una funci&#243;n
Has intentado asignar un valor al resultado de una función.  El resultado de una función se puede asignar a una variable, pero no se puede usar como una variable.  Si deseas asignar un nuevo valor a la propia función, omite los paréntesis \(el operador de llamada de la función\).  En el ejemplo siguiente se muestra una situación en la que se genera este error.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### Para corregir este error  
  
-   No uses el valor del resultado de la llamada a una función como objeto de una *asignación*.  Sin embargo, puedes asignar el resultado de la llamada a una función *a una variable*.  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   O bien, puedes asignar la propia función \(no su valor devuelto\) a una variable.  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## Vea también  
 [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)   
 [Escribir código JavaScript](../../javascript/writing-javascript-code.md)   
 [Funciones](../../javascript/functions-javascript.md)