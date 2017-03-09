---
title: "Error de inferencia del argumento de tipo para el par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; de &#39;&lt;genericproceduresignature&gt;&#39; | Microsoft Docs"
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
  - "vbc32051"
  - "bc32051"
helpviewer_keywords: 
  - "BC32051"
ms.assetid: a9c2a0ce-e225-4549-bfd8-d42df5d16bfd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error de inferencia del argumento de tipo para el par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; de &#39;&lt;genericproceduresignature&gt;&#39;
Error de inferencia del argumento de tipo para el parámetro de tipo '\<typeparametername\>' de '\<genericproceduresignature\>'. El argumento de tipo no se pudo inferir del argumento pasado al parámetro '\<parametername\>'.  
  
 Se ha llamado a un procedimiento genérico sin proporcionar argumentos de tipo y el compilador no puede inferir el tipo que debe pasar a uno de los parámetros.  
  
 Normalmente, cuando se llama un tipo genérico, se proporciona un argumento de tipo para cada parámetro que define el procedimiento genérico. Si no facilita ningún argumento de tipo, el compilador intenta deducir los tipos que se pasan a los parámetros de tipo. Si el contexto de la llamada proporciona información de tipo de datos en conflicto para un parámetro de tipo, se produce un error en la inferencia de tipos.  
  
 El código siguiente puede generar este error.  
  
```  
Public Sub doSomething(Of t)(ByVal arg1 As t(), ByVal arg2 As t) End Sub Call doSomething(6, 42)  
```  
  
 En el ejemplo anterior, el compilador deduce el tipo `Integer` para `t` a partir del valor 42 pasado a `arg2`. Sin embargo, dicha inferencia requeriría que `arg1` fuese del tipo `Integer()`, es decir, una matriz de `Integer` y el valor 6 pasado a `arg1` no coincide con ese tipo.  
  
 **Identificador de error:** BC32051  
  
### Para corregir este error  
  
-   Facilite argumentos de tipo al procedimiento genérico para que el compilador no tenga que deducirlos.  
  
-   Proporcione argumentos normales con tipos que coinciden con los de los argumentos de tipo.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)