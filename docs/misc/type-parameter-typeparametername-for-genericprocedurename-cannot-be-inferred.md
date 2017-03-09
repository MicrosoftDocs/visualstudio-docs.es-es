---
title: "No se puede inferir el par&#225;metro de tipo &#39;&lt;nombrePar&#225;metroTipo&gt;&#39; para &#39;&lt;nombreProcedimientoGen&#233;rico&gt;&#39;. | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inferir el par&#225;metro de tipo &#39;&lt;nombrePar&#225;metroTipo&gt;&#39; para &#39;&lt;nombreProcedimientoGen&#233;rico&gt;&#39;.
Se llama a un procedimiento genérico sin proporcionar una lista de argumentos de tipo y se produce un error en la inferencia de tipos para uno de los argumentos de tipo.  
  
 Cuando se llama a un procedimiento genérico, normalmente se proporciona un argumento de tipo para cada parámetro de tipo definido por el procedimiento. Sin embargo, tiene la alternativa de omitir completamente la lista de argumentos de tipo. Al hacerlo, el compilador intenta inferir el tipo de cada argumento de tipo a partir del contexto de la llamada. Para más información, vea "Inferencia de tipos" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Una posible causa del error de inferencia de tipo es una no coincidencia de clasificación entre un parámetro de tipo y el tipo de llamada. Esto se ilustra en el código siguiente:  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 En el código anterior, las dos llamadas a `findLargest` producen este error, porque el parámetro de tipo `t` llama a una matriz unidimensional, mientras que los argumentos de tipo de los que el compilador infiere las llamadas son una matriz escalar \(`testValue`\) y una matriz bidimensional \(`testMatrix`\).  
  
 **Identificador de error:** BC32050  
  
### Para corregir este error  
  
-   Asegúrese de que los tipos de los argumentos normales son tales que la inferencia de tipo es coherente con los parámetros de tipo declarados para el procedimiento genérico.  
  
     O bien  
  
-   Llame al procedimiento genérico con una lista completa de argumentos de tipo, por lo que no sea necesaria la inferencia de tipos.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)