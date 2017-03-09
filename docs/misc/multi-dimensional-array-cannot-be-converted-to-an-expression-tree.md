---
title: "Una matriz multidimensional no se puede convertir en un &#225;rbol de expresi&#243;n | Microsoft Docs"
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
  - "bc36603"
  - "vbc36603"
helpviewer_keywords: 
  - "BC36603"
ms.assetid: 65eefab7-c7ad-4dcd-bebf-2d16fba9f28f
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una matriz multidimensional no se puede convertir en un &#225;rbol de expresi&#243;n
La mayoría de expresiones se puede convertir en árboles de expresión, pero las matrices multidimensionales no. Por ejemplo, el código siguiente provoca este error:  
  
```vb#  
Module Module1 Sub Main() '' A multi-dimensional array cannot be converted. 'Dim expTree As Expressions.Expression(Of Func(Of Object)) = _ '    Function() New Integer(1, 1) {{1, 2}, {2, 3}} ' A one-dimensional array can be converted. Dim expTree2 As Expressions.Expression(Of Func(Of Object)) = _ Function() New Integer() {1, 2, 3} End Sub End Module  
```  
  
 **Id. de error:** BC36603  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Árboles de expresión en LINQ](http://msdn.microsoft.com/es-es/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)   
 [Cómo: Usar árboles de expresión para crear consultas dinámicas](../Topic/How%20to:%20Use%20Expression%20Trees%20to%20Build%20Dynamic%20Queries%20\(C%23%20and%20Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Matrices multidimensionales en Visual Basic](http://msdn.microsoft.com/es-es/d92cad25-07e2-4d79-8ea4-ab269700f5de)