---
title: "Las operaciones de enlace en tiempo de ejecuci&#243;n no se pueden convertir en un &#225;rbol de expresi&#243;n | Microsoft Docs"
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
  - "vbc36604"
  - "bc36604"
helpviewer_keywords: 
  - "BC36604"
ms.assetid: 6fd66d12-8c99-46e0-9095-fe1b29fd2692
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las operaciones de enlace en tiempo de ejecuci&#243;n no se pueden convertir en un &#225;rbol de expresi&#243;n
Se ha intentado convertir una operación de enlace de tiempo de ejecución en un árbol de expresión. Esta operación no es válida. Por ejemplo, el código siguiente causa este error.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. ' Test(Function(someInstance) someInstance.SomeProperty) End Sub Sub Test(ByVal ex As Expressions.Expression(Of Func(Of Object, Object))) End Sub End Module  
```  
  
 **Identificador de error:** BC36604  
  
## Vea también  
 [Enlace en tiempo de compilación y en tiempo de ejecución](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)   
 [NO ESTÁ EN LA COMPILACIÓN: Árboles de expresión en LINQ](http://msdn.microsoft.com/es-es/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)