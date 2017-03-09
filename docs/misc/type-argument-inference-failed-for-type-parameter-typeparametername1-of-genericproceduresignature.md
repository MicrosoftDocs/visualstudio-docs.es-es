---
title: "Error de inferencia del argumento de tipo para el par&#225;metro de tipo &#39;&lt;typeparametername1&gt;&#39; de &#39;&lt;genericproceduresignature&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32116"
  - "bc32116"
helpviewer_keywords: 
  - "BC32116"
ms.assetid: 6bfb02ec-814a-4b1f-a585-6d902a861d00
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error de inferencia del argumento de tipo para el par&#225;metro de tipo &#39;&lt;typeparametername1&gt;&#39; de &#39;&lt;genericproceduresignature&gt;&#39;
Error de inferencia del argumento de tipo para el parámetro de tipo '\<typeparametername1\>' de '\<genericproceduresignature\>'. El argumento de tipo inferido del argumento pasado al parámetro '\<parametername1\>' entra en conflicto con el argumento de tipo inferido del argumento pasado al parámetro '\<parametername2\>'.  
  
 Se llama a un procedimiento genérico sin ningún argumento de tipo y la inferencia de tipos que se ha intentado ha generado un conflicto de tipos de datos entre los parámetros de tipo.  
  
 Normalmente, cuando se llama un tipo genérico, se proporciona un argumento de tipo para cada parámetro que define el procedimiento genérico. Si no facilita ningún argumento de tipo, el compilador intenta deducir los tipos que se pasan a los parámetros de tipo. Si el contexto de la llamada proporciona información de tipo de datos en conflicto para un parámetro de tipo, se produce un error en la inferencia de tipos.  
  
 El código siguiente puede generar este error.  
  
```  
Public Sub takeTwoValues(Of t)(ByVal x As t, ByVal y As t) End Sub Call takeTwoValues(4, 2.5)  
```  
  
 Dado que el primer argumento hace que el compilador deduzca `Integer` para el parámetro de tipo `t`, mientras que el segundo argumento provoca que se deduzca `Double` para el mismo parámetro de tipo, existe un conflicto con respecto al tipo de datos que se van a pasar a `t`.  
  
 **Identificador de error:** BC32116  
  
### Para corregir este error  
  
-   Facilite argumentos de tipo al tipo genérico para que el compilador no tenga que deducirlos.  
  
    ```  
    Call takeTwoValues(Of Double)(4, 2.5)  
    ```  
  
     Tenga en cuenta que en este caso, cuando los dos argumentos normales son de distintos tipos de datos, el código de llamada debe pasar un argumento de tipo que pueda alojar ambos tipos de datos. En este caso, `Integer` se amplía a `Double`.  
  
     O bien  
  
-   Vuelva a definir el procedimiento genérico para especificar distintos parámetros de tipo para los parámetros normales para que no haya ningún conflicto al deducir los tipos.  
  
    ```  
    Public Sub takeTwoValues(Of t1, t2)(ByVal x As t1, ByVal y As t2)  
    ```  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)