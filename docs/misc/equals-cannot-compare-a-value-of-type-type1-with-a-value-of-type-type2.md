---
title: "&#39;Equals&#39; no puede comparar un valor de tipo &lt;tipo1&gt; con un valor de tipo &lt;tipo2&gt;. | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; no puede comparar un valor de tipo &lt;tipo1&gt; con un valor de tipo &lt;tipo2&gt;.
Un operador `Equals` en una cláusula `Join` o `Group Join` intentó comparar un tipo de datos con otro de una manera no definida. Un ejemplo de esto es una comparación de un valor `Boolean` con un tipo `Date`.  
  
 **Identificador de error:** BC36621  
  
### Para corregir este error  
  
-   Asegúrese de que los valores de cada lado del operador `Equals` se pueden convertir a un tipo de datos común. Algunas opciones para lograrlo son:  
  
    -   Usar la función `CType` para convertir uno o varios de los valores a un tipo específico.  
  
    -   Usar los métodos de conversión o clase <xref:System.Convert> para convertir uno o varios de los valores a un tipo inmutable común.  
  
    -   Convertir los valores en cadenas mediante el método `ToString`.  
  
## Vea también  
 [CType \(Función\)](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)