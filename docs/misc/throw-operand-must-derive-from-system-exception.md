---
title: "El operando &#39;Throw&#39; debe derivar de &#39;System.Exception&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30665"
  - "bc30665"
helpviewer_keywords: 
  - "BC30665"
ms.assetid: 7c228087-39ea-4b30-a410-6ba711e67e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando &#39;Throw&#39; debe derivar de &#39;System.Exception&#39;
El argumento proporcionado a `Throw` debe ser una instancia de `System.Exception` o una instancia de una clase derivada de `System.Exception`.  
  
 **Identificador de error:** BC30665  
  
### Para corregir este error  
  
-   Use un argumento derivado de `System.Exception`, como en el ejemplo siguiente.  
  
    ```  
    Throw New System.Exception("This is an error.")  
    ```  
  
## Vea también  
 [Throw \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Clase de excepción en Visual Basic](http://msdn.microsoft.com/es-es/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Control de excepciones y errores en Visual Basic](http://msdn.microsoft.com/es-es/3e351e73-cf23-40ab-8b60-05794160529e)